---
title: "Installl stalls at 83"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by mulligan.can on 2006-12-24
Ok, I am attempting to install the 6.10 server on a box with a 500mhz p3, 128mb ram and 2x40gb hdd's.

I am trying to use the following partition layout:
drive 1
120mb - ext2 - /boot
480mb - swap
remainder LVM

drive 2
480mb - swap
remainder LVM


I am then creating one volume with the LVM and formatting it as jfs.

Anyway, every time I try and install it hangs at 83% when it is trying to install/copy "linux-kernel-server" over.

Can anyone help me out here? It driving me insane!

(oh and I already validated the cd, its perfect :'()

---

### Post by cilynx on 2006-12-24
For troubleshooting, I would let it autoparition one of the drives and use the default filesystem and see if it makes it through the install.  I would also try burning off another copy of the CD just in case.  Weirder things have happened...

---

### Post by mulligan.can on 2006-12-25
Ok, I have managed to isolate the problem. My bios doesn't support drives over 33822MB (although one of the drives seems to automatically pretend to be that size till after the bios finishes its stuff).

Anyway, see this thread if your interested in helping me out :)

[http://ubuntuforums.org/showthread.php?t=325083](http://ubuntuforums.org/showthread.php?t=325083)

---

