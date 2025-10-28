# Notes:
==============

### Steps:-
1. Create the .NET Project using terminal or automatically and with the needed structure.
 1. We here used the **API/Core/Infrastructure**.
 2. **API** contains the startup configuration (Program.cs, appsettings.json, etc.)
 3. **Core** for entities and products.
 4. **Infrastructure** for dealing with database.
 5. Solution/
    ├── API/                 # -s API (Startup project)
    │   ├── Program.cs
    │   ├── appsettings.json
    │   └── Controllers/
    ├── Infrastructure/      # -p Infrastructure (DbContext project)
    │   ├── Data/
    │   │   └── AppDbContext.cs
    │   └── Entities/
    └── Core/
        └── Models/
2. Create the entities.
 1. It would be better to create a base class for entities `BaseEntity`.
3. Set the entity framework.
 1. maybe using the terminal like `dotnet ef` command.
 2. and use this to add a migration: `dotnet ef migrations add InitialCreate -s API -p Infrastructure`.
4. Set the SQL Server and connect to the app.
5. Configure the entities for migrations.
 1. If you want to configure some entites e.g.Price, you can do it on the context class, or instead you would better create a class to do this for all products e.g. ProductConfigurations in the infrastructure of the project in a specific folder for that.
 2. Create database for created migrations with this command: `dotnet ef database update -s API -p Infrastructure`.
6. Add `ProductsController` with methods `Get`, `Create`, `Update`, `Delete`.
7. Add API Architecture e.g. Repository Pattern.
 1. Add interface `IProductRepository`.
 2. Add the concrete class `ProductRepository`.
 3. Add the service as DI to the **program.cs**.
 4. Use the Repository Pattern in the controller.
 5. drop the current data base if there (and if you need that) using this: `dotnet ef database drop -p Infrastructure -s API`
 6. Seed data to the database.