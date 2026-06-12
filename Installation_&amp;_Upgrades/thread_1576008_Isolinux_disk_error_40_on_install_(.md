---
title: "Isolinux disk error 40 on install :("
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by tankduck on 2010-09-16
Evening all,
Our NAS drive just packed in so I thought I'd quickly build up a ubuntu server. Got two 500gb sata drives in raid mirror trying to install the latest iso of ubuntu server, but it all loads up to the point where you choose what to install, and pretty much whatever you select returns, booting from local disk, isolinux: disk error 40.....hit any key to retry, which of course restarts the system and the horrible sequence starts again :( 

I've just rewritten the disk and its still playing silly buggers :(

Any ideas jumping to mind?

Kris

---

### Post by uRock on 2010-09-16
Have you MD5summed the ISO image?

---

### Post by Rubi1200 on 2010-09-16
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

There can be issues with RAID in Ubuntu:
[https://wiki.ubuntu.com/ReliableRaid](https://wiki.ubuntu.com/ReliableRaid)

---

### Post by tankduck on 2010-09-17
Thanks guys, I have done MD5 check and its fine, I've turned RAID off, and I'm still getting the exact same error :(

---

### Post by tankduck on 2010-09-17
I have just tried with different cd-rom, different belt, tried with different hdd's disconnected (have one ide, and two sata in the case) but its still showing the same error, even if I go to check the cd for defects it goes to a blank screen, says loading from local disk or something then says ISOLINUX disk error 40 ....disk 00

What could this mean?

Kris

---

### Post by Rubi1200 on 2010-09-17
Unless you actually need a RAID setup I think you need to remove any RAID metadata from the drive.

I am trying to find the commands for you and will post back when I have it.

EDIT: So, I am not 100% sure of this, but the poster is very experienced and I think this may contain at least part of the answer for you:
[http://ubuntuforums.org/showpost.php?p=8334643&postcount=4](http://ubuntuforums.org/showpost.php?p=8334643&postcount=4)

If you are unsure or have more questions, please post before trying anything.

---

