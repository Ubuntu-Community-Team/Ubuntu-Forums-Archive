---
title: "Unable to fetch libreoffice-kde (among some others). Help?"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by timonoj on 2016-02-22
Hi guys,

It's been over a week that apparently I'm unable to update certain packages. I tried purging libreoffice altogether, but they're still not available:
```

sudo apt install libreoffice-kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libreoffice-common libreoffice-core libreoffice-style-breeze libreoffice-style-galaxy python3-uno
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast libreoffice-style-human libreoffice-style-oxygen libreoffice-style-sifr
  libreoffice-style-tango konqueror libreoffice-kab
The following NEW packages will be installed:
  libreoffice-common libreoffice-core libreoffice-kde libreoffice-style-breeze libreoffice-style-galaxy python3-uno
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 471 kB/54.1 MB of archives.
After this operation, 215 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Err http://ubuntu.01link.hk/ wily-security/universe libreoffice-style-breeze all 1:5.0.5~rc2-0ubuntu2
  404  Not Found
Err http://ubuntu.01link.hk/ wily-security/universe libreoffice-kde amd64 1:5.0.5~rc2-0ubuntu2
  404  Not Found
E: Failed to fetch http://ubuntu.01link.hk/pool/universe/libr/libreoffice/libreoffice-style-breeze_5.0.5~rc2-0ubuntu2_all.deb  404  Not Found

E: Failed to fetch http://ubuntu.01link.hk/pool/universe/libr/libreoffice/libreoffice-kde_5.0.5~rc2-0ubuntu2_amd64.deb  404  Not Found

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Any ideas why?
Using Kubuntu 15.10.

Thanks a lot!

---

### Post by QIII on 2016-02-22
404 indicates that the resource cannot be found.  It may be that the repository you are trying to access is down or being updated.  Try changing your repos to main and see if that helps.

---

### Post by timonoj on 2016-02-22
Thanks for your reply!
I tried with a different repo in the same location (Hong Kong) and still got the same issue...Let me try a couple more including the main one.

Huh...
```

sudo apt-get update
Get:74 http://hk.archive.ubuntu.com wily-security/multiverse Translation-en [2,806 B]                                              
Get:75 http://hk.archive.ubuntu.com wily-security/restricted Translation-en [2,666 B]                                              
Get:76 http://hk.archive.ubuntu.com wily-security/universe Translation-en [29.5 kB]                                                
Fetched 32.3 MB in 37s (865 kB/s)                                                                                                  
W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/wily-updates/main/source/Sources  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-i386/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

