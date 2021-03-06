# Migration `20200911024442-create-orgcontact`

This migration has been generated by Dave Grace at 9/11/2020, 12:44:42 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
CREATE TABLE "OrgContact" (
    "id" INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    "name" TEXT NOT NULL,
    "street" TEXT NOT NULL,
    "suburb" TEXT NOT NULL,
    "postcode" INTEGER NOT NULL,
    "coverage" TEXT NOT NULL,
    "contactName" TEXT NOT NULL,
    "majorPurpose" TEXT NOT NULL,
    "contactPN" TEXT NOT NULL,
    "meetingTime" DATETIME NOT NULL,
    "meetingTimeFrequency" TEXT NOT NULL,
    "meetingPlace" TEXT NOT NULL,
    "webpage" BOOLEAN NOT NULL,
    "webpageAddress" TEXT NOT NULL,
    "newsletter" BOOLEAN NOT NULL,
    "alpMembers" BOOLEAN NOT NULL,
    "email" TEXT NOT NULL,
    "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP
)

CREATE UNIQUE INDEX "OrgContact.email_unique" ON "OrgContact"("email")
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration ..20200911024442-create-orgcontact
--- datamodel.dml
+++ datamodel.dml
@@ -1,0 +1,34 @@
+datasource DS {
+  // optionally set multiple providers
+  // example: provider = ["sqlite", "postgresql"]
+  provider = "sqlite"
+  url = "***"
+}
+
+generator client {
+  provider      = "prisma-client-js"
+  binaryTargets = "native"
+}
+
+model OrgContact {
+  id                   Int      @id @default(autoincrement())
+  name                 String
+  street               String
+  suburb               String
+  postcode             Int
+  coverage             String
+  contactName          String
+  majorPurpose         String
+  contactPN            String
+  meetingTime          DateTime
+  meetingTimeFrequency String
+  meetingPlace         String
+  webpage              Boolean
+  webpageAddress       String
+  newsletter           Boolean
+  alpMembers           Boolean
+  email                String   @unique
+  createdAt            DateTime @default(now())
+
+
+}
```


