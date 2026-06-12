---
title: "Upgrade Kubuntu"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Oscardisena on 2008-07-07
Hi,

I'm using Kubuntu 8.04. I have installed KDE 3.5.0 and KDE4. I have 47 upgraded packages available, but when I try to do that it gives me an error, this is the error:

[I][COLOR="Blue"]Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `esound-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gettext-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `enscript' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `tcl8.4' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `fdutils' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.2_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `avahi-autoipd': Is a directory
Errors were encountered while processing:
 /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR][/I]

What I have to do to upgrade my Kubuntu?

Thank you,
OG

---

### Post by Partyboi2 on 2008-07-07
Have you tried to reinstall these packages? (*[COLOR=Blue]esound-common, [/COLOR]**[COLOR=Blue]gettext-base, [/COLOR]**[COLOR=Blue]enscript, [/COLOR]**[COLOR=Blue]tcl8.4, [/COLOR]*[I][COLOR=Blue]fdutils)
[/COLOR][/I]
Another thing you could consider is to delete the packages in the local cache archive and let them be downloaded again
```
 sudo rm /var/cache/apt/archives/*
```
```
 sudo apt-get update
```



[I][COLOR=Blue]

[/COLOR][/I]

---

### Post by Oscardisena on 2008-07-07
I tried, but it doesn't work. I also tried to reinstall those packages, but it doesn't work idem.

This is the answer:
```

sudo apt-get install esound-common gettext-base enscript tcl8.4 fdutils
```

[COLOR="Blue"]Reading package lists... Done
Building dependency tree
Reading state information... Done
esound-common is already the newest version.
gettext-base is already the newest version.
enscript is already the newest version.
tcl8.4 is already the newest version.
fdutils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 47 not upgraded.[/COLOR]

---

### Post by abn91c on 2008-07-07
kubuntu  8.04 by default has kde 3.59, if you saying you "installed" 3.5.0 that is a downgrade, hence the errors. Just do in a Konsole sudo aptitude reinstall kubuntu-desktop

---

### Post by Oscardisena on 2008-07-07
What I have is a KDE 3.5.9, KDE 3.5.0 was an error while writing.

I tried ```
sudo aptitude reinstall kubuntu-desktop
``` but it doesn't work.

---

