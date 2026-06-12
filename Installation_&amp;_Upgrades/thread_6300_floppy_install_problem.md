---
title: "floppy install problem"
date: 2004-11-27
forum: Installation &amp; Upgrades
---

### Post by cdevos on 2004-11-27
Hello,
The computer is a Pentium III which has 2 SCSI CD-ROMs (and 2 IDE HD).
I'd like to install warty on the 2nd HD: hdb.
I've checked [http://www.ubuntulinux.org/wiki/InstallWithFloppiesHowto](http://www.ubuntulinux.org/wiki/InstallWithFloppiesHowto) and [http://www.ubuntulinux.org/wiki/InstallFromKnoppixHowto](http://www.ubuntulinux.org/wiki/InstallFromKnoppixHowto).

Here is what I did:
Install sarge with boot floppies, no problem.
Partitions on hdb:
hdb1 = /
hdb5 = swap
hdb6 = /home

Now I would like to replace the sarge install on hdb1 by warty.

So, I did like in the install from knoppix howto:
downloaded debootstrap_0.2.45ubuntu7, decompressed it and typed:
```

DEBOOTSTRAP_DIR=`pwd` ./debootstrap --arch i386 warty / http://archive.ubuntulinux.org/ubuntu warty
```

Here is the error I get:
```
./debootstrap: line 15: pwd/functions: No such file or directory
```

When I check the debootstrap script, line 15 is:
. $DEBOOTSTRAP_DIR/functions

Anybody can help?

Thanks in advance,

-- 
Carl

---

### Post by cdevos on 2004-12-04
Answering to myself.

Here is what I did:
I changed my sources.list to point to the ubuntu server.
Then I dpkg --get-selections > list.packages from my Ubuntu workstation, copied the file to the computer to be installed, and cat list.packages | dpkg --set-selections, then apt-get update followed by apt-get deselect-upgrade.
Some minor gliches I manage to solve myself.

Another (probably better) way to do it would be to make boot floppies for Knoppix:
K Menu --> KNOPPIX --> Utilities --> Create bootfloppies for KNOPPIX.

Then boot from there start knoppix and follow [https://www.ubuntulinux.org/wiki/InstallFromKnoppixHowto](https://www.ubuntulinux.org/wiki/InstallFromKnoppixHowto)

---

