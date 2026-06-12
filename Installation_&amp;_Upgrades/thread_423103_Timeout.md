---
title: "Timeout"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by logicus on 2007-04-25
Hi there

I'm trying to upgrade from a very stable 06.10 ubuntu with KDE.
When i try i get timeout and the upgrade stops.

Here are the error messages:

The none english  messages simply states that it times out.

The repos are Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg) Kunne ikke forbinde til packages.freecontrib.org:80 (88.191.33.6) grundet tidsudløb
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/i18n/Translation-da.bz2](http://packages.freecontrib.org/plf/dists/dapper/free/i18n/Translation-da.bz2) Kunne ikke forbinde til packages.freecontrib.org:80 (88.191.33.6) grundet tidsudløb
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/i18n/Translation-da.bz2](http://packages.freecontrib.org/plf/dists/dapper/non-free/i18n/Translation-da.bz2) Kunne ikke forbinde til packages.freecontrib.org:80 (88.191.33.6) grundet tidsudløb


Any suggestion as to how to fix it and is the 07.04 a stable system ?

Sincerely

Peter

---

### Post by jfinkels on 2007-04-25
> **logicus said:**
> Hi there

I'm trying to upgrade from a very stable 06.10 ubuntu with KDE.
When i try i get timeout and the upgrade stops.

Here are the error messages:

The none english  messages simply states that it times out.

The repos are Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg) Kunne ikke forbinde til packages.freecontrib.org:80 (88.191.33.6) grundet tidsudløb
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/i18n/Translation-da.bz2](http://packages.freecontrib.org/plf/dists/dapper/free/i18n/Translation-da.bz2) Kunne ikke forbinde til packages.freecontrib.org:80 (88.191.33.6) grundet tidsudløb
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/i18n/Translation-da.bz2](http://packages.freecontrib.org/plf/dists/dapper/non-free/i18n/Translation-da.bz2) Kunne ikke forbinde til packages.freecontrib.org:80 (88.191.33.6) grundet tidsudløb


Any suggestion as to how to fix it and is the 07.04 a stable system ?

Sincerely

Peter

It looks like you are trying to update through repositories for Ubuntu 6.06, Dapper Drake. Post the output of this command:
```

cat /etc/apt/sources.list

``` 

And yes, 7.04 is a stable system.

---

### Post by bapoumba on 2007-04-25
> **logicus said:**
> 
The repos are Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg) Kunne ikke forbinde til packages.freecontrib.org:80 (88.191.33.6) grundet tidsudløb
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/i18n/Translation-da.bz2](http://packages.freecontrib.org/plf/dists/dapper/free/i18n/Translation-da.bz2) Kunne ikke forbinde til packages.freecontrib.org:80 (88.191.33.6) grundet tidsudløb
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/i18n/Translation-da.bz2](http://packages.freecontrib.org/plf/dists/dapper/non-free/i18n/Translation-da.bz2) Kunne ikke forbinde til packages.freecontrib.org:80 (88.191.33.6) grundet tidsudløb

hello,

freecontrib do not support ubuntu packages anymore. You can use the [medibuntu]("http://medibuntu.sos-sts.com/") repos instead (some of the previous plf team are in medibuntu now).

---

