---
title: "Update error"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by SerafeimG on 2010-08-12
I am running Ubuntu 10.04 under a 64-bit laptop.

My update manager recommends the follow updates:
libmysqlclient16
mysql-common

When I click on "Install Updates" button an error comes up with the following text:


**************************************************************************

W: Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-common_5.1.41-3ubuntu12.6_all.deb](http://gr.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-common_5.1.41-3ubuntu12.6_all.deb)
  Could not connect to gr.archive.ubuntu.com:80 (147.102.222.211). - connect (110: Connection timed out)


W: Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/libmysqlclient16_5.1.41-3ubuntu12.6_amd64.deb](http://gr.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/libmysqlclient16_5.1.41-3ubuntu12.6_amd64.deb)
  Unable to connect to gr.archive.ubuntu.com:http:
**************************************************************************



When I click on "Check" button the following error comes up:


**************************************************************************
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to gr.archive.ubuntu.com:80 (147.102.222.211). - connect (110: Connection timed out)
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.
**************************************************************************


Any recommendations in order to fix this errors and manage to install the recommended updates?

Thank you all in advance.

---

### Post by mörgæs on 2010-08-12
I don't think I can explain it otherwise than Ubuntu does:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Wait a few hours, boot the machine and try again.

---

### Post by kvergos on 2010-08-12
I'm having the same exact problem for about 15 days (on two laptops).
Isn't there some other server for these files?

---

### Post by kvergos on 2010-08-12
So it seems that the Greeks are on summer vacation so either wait for September or do what I did. Open software sources from the system menu and chose a different server. The first one in Germany worked for me.

---

### Post by SerafeimG on 2010-08-14
Thank you kvergos. You seem to be right. I changed to Main server and made the updates normally. Thanks a lot. Maybe I will change back to the Greek server at the middle of September...

---

