# Build aşaması
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
WORKDIR /app

# Proje dosyasını kopyalayın ve restore edin
COPY *.csproj ./
RUN dotnet restore

# Tüm dosyaları kopyalayın ve yayınlama yapın
COPY . ./
RUN dotnet publish -c Release -o out

# Runtime aşaması
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "PersonalFinance.API.dll"]
