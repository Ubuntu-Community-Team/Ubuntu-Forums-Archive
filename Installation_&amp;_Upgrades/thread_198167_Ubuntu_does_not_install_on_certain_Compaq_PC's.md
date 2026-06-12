---
title: "Ubuntu does not install on certain Compaq PC's"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by TylerM on 2006-06-16
I am running a crappy Compaq PC that I would like to make useful my installing Ubuntu on it.  I have found other people that have tried to install Linux on a Compaq and it doesn't work.  The post below is the same ***exact*** problem I get when trying to install 6.06 (though I have a 2.7 GHz PC with 1GB of RAM), and I think it is a hardware/coding problem and not a software problem because I have tried 6 different images and shipped copies.  Any suggestions?

"Hi! I just received my ubuntu disks in the mail today (thank you! ) and I've been trying to load the live cd, but I'm having some problems. Everything seems to work fine until I get to the "loading kernel" part. As soon as I do, the computer reboots. I've tried typing in "live noapic nolapic" but the same thing happens. I'm stumped.

My computer is a compaq presario with a 2.53 GHz Celeron and 248MB of RAM (kinda slow I know, but it's all I could afford.) Any help would be most appreciated!" - *scapermoon*

UPDATE:  Fixed one problem by adding "linux acpi=off" but then it loads some of the drivers, stops at mounting root filesystem, and then a black screen with "[*] Buffer I/O error on device hdb, logical block 39102336" (*number varies).  Then I am allowed to type a command once again.  I have no idea what to do!

Any help would be appreciated.

---

### Post by TylerM on 2006-06-16
Bump

---

### Post by stoneguy on 2006-06-17
Try adding ide=nodma to the boot line as well.

248 (?) of RAM may be marginal, although 384 is sufficient, even on an 400Mz and 500Mz systems. RAM can be a showstopper. CPU speed will just tax your patience.

---

