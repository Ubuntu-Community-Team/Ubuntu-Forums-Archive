---
title: "[SOLVED] How do i uninstall Ubuntu?"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by gmanlivid on 2007-08-07
I was just wondering, how do i uninstall ubuntu off my internal drive. i managed to install it a while back and got it to boot with Grub 1.5 alongside XP but now the OS selection is getting a bit annoying cos i hardly use Ubuntu for a few reasons.

and i think i messed up somewhere. i got a 60gig internal, and when i was creating partitions, i didn't want to lose my windows partition so i erased my second partition and created ubuntu partitions. but.....that leaves me with like 20 gigs of space lost that i can't unlock cos they're at the end of the drive. should have resized my windows parition....hmm.

i was also wondering, i saw shots of Beryl and i think its awesome. i wanna get it but is it possible for me to install a linux OS on an external drive without killing my current partition on it? i just bought a 320gig and i got alot on it so i don't wanna lose anything.

thx

oh yeah. umm is it possible to just delete the Ubuntu partitions and go back to normal booting? or do i have to do a whole lot of work to get it off secureley.

---

### Post by wjp.reg on 2007-08-07
> **gmanlivid said:**
> I was just wondering, how do i uninstall ubuntu off my internal drive. i managed to install it a while back and got it to boot with Grub 1.5 alongside XP but now the OS selection is getting a bit annoying cos i hardly use Ubuntu for a few reasons.

and i think i messed up somewhere. i got a 60gig internal, and when i was creating partitions, i didn't want to lose my windows partition so i erased my second partition and created ubuntu partitions. but.....that leaves me with like 20 gigs of space lost that i can't unlock cos they're at the end of the drive. should have resized my windows parition....hmm.

i was also wondering, i saw shots of Beryl and i think its awesome. i wanna get it but is it possible for me to install a linux OS on an external drive without killing my current partition on it? i just bought a 320gig and i got alot on it so i don't wanna lose anything.

thx

delete the linux partition(s) so that the 20gigs becomes part of the free space.

To restore your Windows boot, run the recovery console and enter ```
fixmbr
``` so you can boot into windows again.

You should be able to expand your windows partition from the disk manager utility to encompass the free space you created.

to install linux on a second drive do a google search for ¨installing linux on a second drive¨; there are lots of tutorials.

---

### Post by LaRoza on 2007-08-07
Please get the Super Grub Disk, BEFORE deleting the partition, check my sig.

---

### Post by gmanlivid on 2007-08-07
thx. will try them as soon as i have time.

---

### Post by gmanlivid on 2007-08-08
> **LaRoza said:**
> Please get the Super Grub Disk, BEFORE deleting the partition, check my sig.

ok i got the super grub disk, now what? i had a look at it and i'm clueless which option to choose.

---

### Post by wjp.reg on 2007-08-08
> **gmanlivid said:**
> ok i got the super grub disk, now what? i had a look at it and i'm clueless which option to choose.

That was the impression I had after having a look at it myself; no offence :confused:

You could most likely use any Live CD with gparted (my preference) and remove the linux partitions, thereby creating free space which can then be used to expand your windows ntfs.

---

### Post by gmanlivid on 2007-08-08
oh thx. nvm, i managed to use the GRUB disk. everything is back to normal now and i got my freespace back. contemplating if i want to re-install ubuntu properly of if i want to go get the live cd for beryl.

---

