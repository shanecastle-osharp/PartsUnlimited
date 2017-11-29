#FROM microsoft/aspnetcore-build:2.0 AS build-env
#WORKDIR /app
#
## Copy csproj and restore as distinct layers
#COPY *.csproj ./
#RUN dotnet restore
#
## Copy everything else and build
#COPY . ./
#RUN dotnet publish -c Release -o out
#
## Build runtime image
#FROM microsoft/aspnetcore:2.0
#WORKDIR /app
#COPY --from=build-env /app/out .
#ENTRYPOINT ["dotnet", "PartsUnlimitedWebsite.dll"]


FROM microsoft/aspnetcore-build:2.0

WORKDIR /app
EXPOSE 12023

COPY . ./

RUN rm -r node_modules
RUN npm install
RUN npm install node-sass -g
RUN npm rebuild node-sass -g
RUN npm install grunt -g

RUN dotnet build

CMD dotnet run
