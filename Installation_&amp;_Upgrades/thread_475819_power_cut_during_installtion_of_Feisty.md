---
title: "power cut during installtion of Feisty"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2007-06-16
My power went out with about 5 minutes to go on a Feisty upgrade (from Edgy). 
The computer restarted fine, but I don't know if the upgrade needs to be done again or how to go abotu picking up where I left off. I'm not even sure where to check if I'm on Edgy or Feisty (sources.list has been upgraded to Feisty, at least).

---

### Post by Pumalite on 2007-06-16
> **pickarooney said:**
> My power went out with about 5 minutes to go on a Feisty upgrade (from Edgy). 
The computer restarted fine, but I don't know if the upgrade needs to be done again or how to go abotu picking up where I left off. I'm not even sure where to check if I'm on Edgy or Feisty (sources.list has been upgraded to Feisty, at least).

Thank God and go on. Wait until the next upgrade.

---

### Post by floke on 2007-06-16
Personally I'd go for a fresh install.

---

### Post by pickarooney on 2007-06-16
Ack, I waited two months before I finally decided to go ahead and accept the Wanna Upgrade button in Adept, thinking "there's nothing useful in feisty, leave it" only to end up with an inevitably screwed install.

I tried **sudo dpkg --configure -a** but it buggered up after 5 minutes trying to set up smartmontools.

I'm wavering between both suggestions...

---

### Post by openprivacy on 2007-07-31
You're lucky - I think I'm in much worse shape :( after an install sequence was interrupted by having the lid closed of my wife's Thinkpad 600x that was running Edgy & Xubuntu before the upgrade.

Now it won't boot from hard disk nor from a live CD (edgy or feisty).

I get:
[INDENT]```

invalid compressed format (err=1)
VFS: Cannot open root device "<NULL>" or unknown-block(104,1)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)
```[/INDENT]

I've tried adding 'root=/dev/hda5' and 'root=/dev/hda1' and 'root=ram' but to no avail.  For example, with 'root=/dev/hda1' the error message is essentially the same, except for:
[INDENT]```
VFS: Cannot open root device "hda1" or unknown-block(0,0)
```[/INDENT]

Some similar forum topics suggest editing grup or initrd, but I can't even get that far (or maybe I don't understand.)

Is there hope?

---

### Post by Pumalite on 2007-07-31
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by openprivacy on 2007-08-01
Thank you, Pumalite.  The SystemRescueCD looks like it may do the trick, though it may take me a bit to figure out just how.  What I really want to do now is restart the Ubuntu upgrade, perhaps from a CD, but I'm not sure how to proceed.  I might just opt for backing everything up (again) and starting from scratch - painful, but it will work.

Thanks again!
=Fen

---

### Post by Pumalite on 2007-08-01
Try the rescue CD first. Is not that hard. If not; your last option sounds good.  As for the upgrade; if I were you, i'd wait for the stable release in October.

---

