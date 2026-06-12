---
title: "[SOLVED] Upgrade Errors"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by Spoken on 2008-05-27
IMPORTANT NOTE!!!!
do not "encourage" me to do a fresh install, i cant and dont want to for certain reasons, so please, dont waste my time
IMPORTANT NOTE!!!!

alright, currently i'm running ubuntu 7.04 but i am trying to upgrade to 7.10.  but when when i open update manager and hit "check" i get this error prompt which states the following...

==================================
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
==================================

which is followed by this output

```

cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

```

---

### Post by iaculallad on 2008-05-27
> **Spoken said:**
> IMPORTANT NOTE!!!!
do not "encourage" me to do a fresh install, i cant and dont want to for certain reasons, so please, dont waste my time
IMPORTANT NOTE!!!!

alright, currently i'm running ubuntu 7.04 but i am trying to upgrade to 7.10.  but when when i open update manager and hit "check" i get this error prompt which states the following...

==================================
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
==================================

which is followed by this output

```

cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

```

Go to System->Administration->Software Sources and uncheck the "Installable from CD-ROM/DVD option located under the "Ubuntu Software" tab. And be sure that Main, Universe, Restricted, and Multiverse is checked/enabled.

Then restart your upgrade.

---

### Post by Spoken on 2008-05-27
ok, now when i hit "check" , i dont get any errors, which is good.

BUT!!! when i attempt to do the upgrade and the process gets to the step called "modifying software channels" i get this error

```

Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

```

---

### Post by iaculallad on 2008-05-27
> **Spoken said:**
> ok, now when i hit "check" , i dont get any errors, which is good.

BUT!!! when i attempt to do the upgrade and the process gets to the step called "modifying software channels" i get this error

```

Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

```

On your terminal:

Code:

> update-manager -d

then do the upgrade process again.

---

### Post by zvacet on 2008-05-27
System->Administration->Software Sources and select main server

---

### Post by Spoken on 2008-05-27
alright, after switching it to "main server" , it has proceeded past the first couple steps and no errors yet, i bet that did the trick. thank you very much.

---

