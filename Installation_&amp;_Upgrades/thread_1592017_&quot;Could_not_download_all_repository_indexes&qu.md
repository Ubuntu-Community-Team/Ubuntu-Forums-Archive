---
title: "&quot;Could not download all repository indexes&quot;"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Drumber on 2010-10-10
Trying to upgrade from 10.04 to 10.10 but get the error "Could not download all repository indexes". Which looks something like this:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

[QUOTE]Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (110: Connection timed out)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Unable to connect to gb.archive.ubuntu.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.[/QUOTE]

Does anyone know how I can fix this?

---

### Post by sveterv on 2010-10-10
"connection timed out" - it means your local server (gb.archive.ubuntu.com) is off or is overloaded, because too many people is doing upgrades right now :) using this server. 

GB (UK) server is probably also official server for Ubuntu all around the world, so changing it to any other may have sense even without those few days in a year when people upgrade and install new Ubuntu versions like today.

You can wait till tomorrow or change local server (repository) to some other country use Synaptic for doing so.

Synaptic->Settings->Repositories->Pick other server from the list than Local Mirror for Great Britain.

---

### Post by Drumber on 2010-10-10
> **sveterv said:**
> "connection timed out" - it means your local server (gb.archive.ubuntu.com) is off or is overloaded, because too many people is doing upgrades right now :) using this server. 

GB (UK) server is probably also official server for Ubuntu all around the world, so changing it to any other may have sense even without those few days in a year when people upgrade and install new Ubuntu versions like today.

You can wait till tomorrow or change local server (repository) to some other country use Synaptic for doing so.

Synaptic->Settings->Repositories->Pick other server from the list than Local Mirror for Great Britain.

Ok thanks. Wasn't sure if it was a problem at my end or not.

---

