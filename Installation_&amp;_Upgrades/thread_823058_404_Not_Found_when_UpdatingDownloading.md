---
title: "404 Not Found when Updating/Downloading"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Cooper87 on 2008-06-08
I finished updating to 7.10 and now it seems every time I attempt to update, upgrade, or download I get this problem:

```
josh@laptop:~$ sudo aptitude update
Ign http://ca.archive.ubuntu.com gutsy Release.gpg
Ign http://ca.archive.ubuntu.com gutsy/main Translation-en_CA
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates Release.gpg
Ign http://ca.archive.ubuntu.com gutsy-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy Release 
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_CA
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_CA
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com gutsy-security Release
Ign http://ca.archive.ubuntu.com gutsy-updates Release
Ign http://ca.archive.ubuntu.com gutsy/main Packages
Ign http://ca.archive.ubuntu.com gutsy/restricted Packages
Ign http://ca.archive.ubuntu.com gutsy/main Sources
Ign http://ca.archive.ubuntu.com gutsy/restricted Sources
Ign http://ca.archive.ubuntu.com gutsy/universe Packages
Hit http://security.ubuntu.com gutsy-security/main Packages
Ign http://ca.archive.ubuntu.com gutsy/universe Sources
Ign http://ca.archive.ubuntu.com gutsy/multiverse Packages
Ign http://ca.archive.ubuntu.com gutsy/multiverse Sources
Ign http://ca.archive.ubuntu.com gutsy-updates/main Packages
Ign http://ca.archive.ubuntu.com gutsy-updates/restricted Packages
Ign http://ca.archive.ubuntu.com gutsy-updates/multiverse Packages
Ign http://ca.archive.ubuntu.com gutsy-updates/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Ign http://ca.archive.ubuntu.com gutsy-updates/restricted Sources
Err http://ca.archive.ubuntu.com gutsy/main Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/restricted Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/main Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/restricted Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/universe Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/universe Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/multiverse Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/multiverse Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/main Packages
  404 Not Found
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Err http://ca.archive.ubuntu.com gutsy-updates/restricted Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/multiverse Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/main Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/restricted Sources
  404 Not Found
Fetched 1B in 1s (1B/s)
Reading package lists... Done

```

I'm stumped. I used update for example purposes, but all downloads come up this way as well. I couldn't find anything on the internet or on these forums before posting, so any help at all would be great. Thanks.

---

### Post by Partyboi2 on 2008-06-08
Have you tried changing the server? (Systen>Admin>Software Sources)

---

### Post by gfg on 2008-06-08
Apperantly the Canadian mirrors are down. You can try changing mirrors in software sources, or just wait until the mirrors are back up.

---

### Post by Loonygrizzly on 2008-06-08
I also have this problem, I just installed ubuntu yestarday and find I can't play any media, so when i try to download codecs, it gives me the 404 no found in an error message

---

### Post by Cooper87 on 2008-06-08
I tried changing to the main server, and it notified me with a flashy dialog that told me I would have to install some updates (which is what I was trying to do anyway). While installing the updates I encountered the same problem with 404 not found.

---

