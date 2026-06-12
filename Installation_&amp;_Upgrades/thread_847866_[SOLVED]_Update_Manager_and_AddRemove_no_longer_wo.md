---
title: "[SOLVED] Update Manager and Add/Remove no longer works"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by s3than on 2008-07-03
Hi I started using Ubuntu the other week and it&#347; been fine now the update manager times out. If I go to a terminal and type the following

sudo apt-get clean all

then 

sudo apt-get update 

I get the following I have changed repositories to main and aus and get the same results.

Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release.gpg     
  Could not connect to au.archive.ubuntu.com:80 (91.189.88.31), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release.gpg
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-security Release.gpg
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-security/main Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-security/restricted Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-security/universe Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-security/multiverse Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Reading package lists... Done
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (91.189.88.31), connection timed out

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


I can provide my source.list if required, Thanks in advance Tim

PS yes I am on the internet

---

### Post by iaculallad on 2008-07-03
Try changing your Download Server.

System->Administration->Software Sources, under the "Ubuntu Software" tab-> set "Main Server" as your "Download From" server. Click on close button and open your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by s3than on 2008-07-03
That worked thank you very much, thought Id tried that but it works now.  Thanks very much

---

