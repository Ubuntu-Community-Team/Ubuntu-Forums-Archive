---
title: "Post install mounting"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by ProbablyX on 2008-04-17
Hi!

I just installed Kubuntu 8.04 on my amd64.

The install went on fine but now when I bootup my /home and /media and not even /boot have been mounted!

So either I must mount them myself or "die trying"...

Is there anyway to fix this?

Also GRUB boots hd(1,0) thought its hd 0 I use so I have to press e and change it. Can that be causing this?

Thanks!

---

### Post by ProbablyX on 2008-04-17
Hi again!

Ive managed to remove the boot splash (which just generates a black screen) and found this:

After a while fsck wants to check my harddrives, it OKs the two first then goes on my my /home (which is lime 300GB) lists it as clean then makes a new line with a "_" after that the HDD starts "chewing" for like 5-10 minutes after which this appears:

fsck exit with error code 1


Could this be what is causing the error? The /home partition was made by my previous distro (debian) but it can be mounted manually and works just fine.

Thanks!

PS. Also my fstab contains GUID instead of /dev/hdc* - is that normal?

---

### Post by ProbablyX on 2008-04-17
OK!

I removed the UUID stuff from fstab and replaced it with /dev. Everything mounts now, and that 5 min delay is completely gone. The system boots up in no time!

---

### Post by ProbablyX on 2008-04-18
OK!

So everytime I boot I have this error with GRUB messing up hd1 and hd0 right?

So finally I swapped my boot prio in the BIOS and whoo! GRUB boots fine but now Linux cant find my partitions again!

HOWEVER: I tried moving back the old fstab with the UUID stuff - and that works! But not the /dev/hd* file!

Is this a bug or sumt I should report?

---

