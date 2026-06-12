---
title: "Installing Synology Cloudstation on Ubuntu"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by rob.farrow on 2013-11-03
I am a new Ubuntu user and have downloaded a package from Synology for their Cloudstation application. I can download it and extract it - but can't figure out how to run the "Install" script. It doesn't seem to have a file extension.

Does anyone have experience setting this up on Ubuntu?

Thanks

---

### Post by sanderj on 2013-11-03
Download Cloudstation from (for example) [http://www.synology.com/support/download.php?lang=enu&b=2%20bays&m=DS713%2B](http://www.synology.com/support/download.php?lang=enu&b=2%20bays&m=DS713%2B)
Unpack the tgz
Open a terminal and go into the directory that contains the three files:

```
sander@flappie:~/Downloads/CloudStation-Linux-Installer-2570$ ll
total 30440
drwxrwxr-x  2 sander sander     4096 nov  3 22:18 ./
drwxr-xr-x 15 sander sander    12288 nov  3 22:18 ../
-rw-rw-r--  1 sander sander 31142595 okt  7 12:17 CloudStation.spkg
-rwxrwxr-x  1 sander sander      533 okt  7 12:17 install*
-rw-rw-r--  1 sander sander      770 okt  7 12:17 README
sander@flappie:~/Downloads/CloudStation-Linux-Installer-2570$
```

In that directory, type:

```
./install
```

HTH

---

