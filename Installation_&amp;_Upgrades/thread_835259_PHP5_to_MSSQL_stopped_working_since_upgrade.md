---
title: "PHP5 to MSSQL stopped working since upgrade"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by caban on 2008-06-20
I recently upgraded from 7.10 to 8.04.

Ever since this upgrade, php5-sybase (via FreeTDS) connections using mssql_connect just returns a Warning that it was unable to connect.

Warning: mssql_connect(): Unable to connect to server: ALIAS in Script.php on line 5

I have Perl scripts on this same system that connect via dbi:Sybase (FreeTDS) to that same server ALIAS, flawlessly.

Any ideas on what went wrong during the upgrade?

Thank you

---

