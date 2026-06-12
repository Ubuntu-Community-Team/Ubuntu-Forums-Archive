---
title: "Mysql_connect Error, Could Anybody Tell Me When This Error Comes"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by krisvamc on 2007-05-03
****

Hi,

I am trying to compile one file. I am getting mysql error.

Could anybody tell me when this error comes and how to rectify this.

[B]The error is :

handling.cc: In function ‘bool CreateDatabase()’:
handling.cc:65: error: ‘mysql_connect’ was not declared in this scope
handling.cc: In function ‘bool OpenDatabase()’:
handling.cc:122: error: ‘mysql_connect’ was not declared in this scope
make: *** [handling.o] Error 1[/B]

kris.

---

### Post by az on 2007-05-03
It looks like you need a mysql library or something.  libmysqlclient15-dev?

apt-cache search mysql|grep dev
libmysqlclient15-dev - mysql database development files
gambas - Visual development environment for the Gambas programming language
libghc6-hdbc-dev - Haskell Database Connectivity, GHC6 package
libghc6-hdbc-odbc-dev - unixODBC HDBC (Haskell Database Connectivity) Driver for GHC
libghc6-hdbc-postgresql-dev - PostgreSQL HDBC (Haskell Database Connectivity) Driver for GHC
libghc6-hdbc-sqlite3-dev - Sqlite v3 HDBC (Haskell Database Connectivity) Driver for GHC
libghc6-hsql-dev - Multi-Database Interface System for Haskell
libghc6-hsql-mysql-dev - Multi-Database Interface System for Haskell
libghc6-hsql-odbc-dev - Multi-Database Interface System for Haskell
libghc6-hsql-postgresql-dev - Multi-Database Interface System for Haskell
libghc6-hsql-sqlite-dev - Multi-Database Interface System for Haskell
libghc6-hsql-sqlite3-dev - Multi-Database Interface System for Haskell
libgnademysql-dev - GNat Ada Database Environment - MySQL programming interface
libgnadeodbc-dev - GNat Ada Database Environment - ODBC programming interface
libgnadepostgresql-dev - GNat Ada Database Environment - PostgreSQL programming interface
libgnadesqlite-dev - GNat Ada Database Environment - SQLite programming interface
liblua5.1-sql-mysql-dev - luasql development files for the lua language version 5.1
libmysql++-dev - mysql C++ library bindings (development)
libmysql-ocaml-dev - OCaml bindings for MySql
libsimpledb-dev - C++ ODBC database API
libsqldbc75-dev - Development package for the SQLDBC interface to the MaxDB database system
libsqlod75-dev - Development package for the ODBC interface to the MaxDB database system
libsqlxx-dev - C++ classes for database access via ODBC
libterralib1-dev - A C++ library for Geographical Information Systems -- development package
libtntdb-dev - Development headers for tntdb
libwww-dev - The W3C WWW library - development files
libwww-ssl-dev - The W3C WWW library - development files (SSL support)
sqlrelay-dev - SQL Relay C and C++ APIs
tora - A graphical toolkit for database developers and administrators

---

### Post by krisvamc on 2007-05-03
The library you have mentioned is already installed

---

