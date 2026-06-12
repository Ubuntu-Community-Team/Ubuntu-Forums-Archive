---
title: "problem in installing CGI::SESSION 4.43"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by anjana513 on 2011-03-18
Hi I installed CGI::Session 3.95 yesterday. I realized its a old version and hence downloaded CGI::Session 4.43 today.

When i run perl Makefile.PL , i get the following message

anjana513@ubuntu:~/Desktop/CGI-Session-4.43$ perl Makefile.pl
Can't open perl script "Makefile.pl": No such file or directory
anjana513@ubuntu:~/Desktop/CGI-Session-4.43$ perl Makefile.PL
----------------------------------------
#### WARNING ####

If you are using custom CGI::Session drivers they may not be compatible
with the current driver specifications. You will need to make some changes
to your drivers' code before proceeding with this installation to make it
compatible with CGI::Session 4.x.

Fortunately, current driver specifications are a lot easier to adapt to.
Should you have any assistance re-coding your current drivers, please let
me know.

Current driver specs are documented in CGI/Session/Driver.pm

#### TESTING #####

You are encouraged to run tests for the backend you will be using. The
database backends that need a customized connection string won't run by
default. To run them, some environment variables must be set.

The simplest method is to use the standard "DBI_DSN/DBI_USER/DBI_PASS"
environment variables.

Otherwise, you can set these variables: 
For PostgreSQL:
    CGISESS_PG_DSN
    CGISESS_PG_USER
    CGISESS_PG_PASS

For MySQL:
    CGISESS_MYSQL_DSN
    CGISESS_MYSQL_USER
    CGISESS_MYSQL_PASS
    CGISESS_MYSQL_SOCKET

----------------------------------------
Warning: Module::Metadata::Changes's ini.report.pl failed to generate or update Changelog.ini. 
----------------------------------------
WARNING: EXTRA_META is not a known parameter.
'EXTRA_META' is not a known MakeMaker parameter name.
Writing Makefile for CGI::Session

How do i solve this issue.
Please help.

Anjana

---

