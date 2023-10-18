# MTS Shop Database with Prisma

## Introduction

Welcome to the MTS Shop Database! This project uses Prisma as an Object-Relational Mapping (ORM) tool to interact with the database. It's designed to support the data needs of the MTS Shop application.

## Prerequisites

Before you get started, make sure you have the following prerequisites installed:

-   Node.js
-   Prisma CLI
-   PostgreSQL (or your preferred database system)

## Installation

1. Clone this repository to your local machine.

```shell
git clone https://github.com/pathan-mehedi/mts-shopDB-prisma.git
```

2. Install the project dependencies.

```
cd mts-shopDB-prisma
npm install
```

3. Configure your database connection in the `schema.prisma` file. Replace `<your-database-name>` with your actual database name (e.g., "mts_shopDB-prisma").

```prisma
// schema.prisma
generator client {
  provider = "prisma-client-js"
  output   = "./node_modules/@prisma/client"
}

// ...

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL") // Replace with your database connection URL
}

// ...
```

4. Generate the Prisma Client.

```shell
npx prisma generate
```

## Usage

Now that you've set up the MTS Shop database with Prisma, you can use the Prisma Client to interact with your database. You can define models and create, read, update, or delete records.

You can run Prisma commands like:

-   `npx prisma db push` to apply database schema changes.
-   `npx prisma generate` to regenerate the Prisma Client.
-   Use the Prisma Client to perform database operations in your application.

```javascript
const { PrismaClient } = require("@prisma/client");
const prisma = new PrismaClient();

async function main() {
    // Your database operations here
    const user = await prisma.user.create({
        data: {
            name: "John Doe",
            email: "john@example.com",
        },
    });

    console.log("User created:", user);
}

main()
    .catch((e) => {
        throw e;
    })
    .finally(async () => {
        await prisma.$disconnect();
    });
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

```
The README file now includes the updated repository link.
```
