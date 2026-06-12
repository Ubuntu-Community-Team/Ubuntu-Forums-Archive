---
title: "Dualboot advice"
date: 2005-11-06
forum: Installation &amp; Upgrades
---

### Post by ThomThom on 2005-11-06
Hi.
I'd like to install and try Ubuntu on a system dualbooting with WindowsXP. However I would like to get some advice before I install as I tried to dualboot with Linspire once and got an horrible screen of 07s running down my screen. Something I eventually managed to fix by restoring the mbr.

I have 2 harddrives in my computer. One primary 120GB HD partitioned intoa few partition for various purposes and a backup HD of 40.

I thought of installing Ubuntu onto a spare 10GB partition of my primary HD and set up the dualboot as described in this article: [http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49](http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49)

What I am wondering is if it will work as described in that article if I install to a partition on the same drive as XP, or does it have to be on a separate disk. What was a bit unclear to me was wheter the Ubuntu installer would install the boot manager to the start of the disk or the start of the partition.

I assume that it would not work if it installed to the start of the disk as it would overwrite the windows boot manager, right?

But it would work if it installed to the beginning of the partition?

Just want to make sure I understand the process before I do anything.


I could resize and add another partition to the secondary HD, but it's nearly full so it would involve reorganizing my data quite a bit.

---

### Post by peanut butter on 2005-11-06
linux can be on its own partition (even an extended one:confused: ) and dosen't need a separat HD (hard drive).
Before you start, plan your partitions so you would probably want the following:

10gb     Linux
512 mb  Linux Swap (you must have this )
extra     Windows

the ubuntu installerisstill text based and you should know that you must use expert mode for the partitioner.:cool: 

:confused: if there is something by this it means you dont need to know what it is.

---

### Post by ThomThom on 2005-11-07
I'm trying to figure if I can perform the type of installation described in that article I linked to. Will the Ubuntu installer allow me to place to boot manager to the boot sector of my secondary HD?

---

### Post by x__dark on 2005-11-07
is the problem with GRUB maybe?

---

### Post by ThomThom on 2005-11-07
There is no problem. But I've had problems with Linux dualboot before so I just wanted to ask a couple of questions before I did anything this time.

---

### Post by metoo on 2005-11-07
Pardon me, you want to install the Linux system on the 1st HD and the bootloader for it on the 2nd HD?

Oh well, probably possible (it works the other way around as well), but this is screwed up.

Just install grub to the mbr of the 1st HD. It will most likely detect your windows system automatically.

And if all goes wrong (not likely), you can re-install the mbr with windows (as you once did).
Fish in the forums how to do this. To be save, create a boot floppy first, if you don't have a full win recovery CD (but still a floppy drive in the system).

---

### Post by dudus on 2005-11-07
I had some problems trying this in Hoary. It seems that windows **must** be in the primary hd or it won't boot.

So you have 2 hd's right?

the hd that you will boot must be the one with windows. Even if you overwrite the windows MBR with the ubuntu one.

I'm not sure if it is needed but I would intall /boot on the same disc as windows and than overwrite the mbr. and install / on the other disc.

If you break your winxp box trying this as I did, no need to worry. Just pop in the win xp cd, acces the repair prompt and type fixmbr.

---

### Post by ThomThom on 2005-11-07
[QUOTE=metoo]Pardon me, you want to install the Linux system on the 1st HD and the bootloader for it on the 2nd HD?

Oh well, probably possible (it works the other way around as well), but this is screwed up.

Just install grub to the mbr of the 1st HD. It will most likely detect your windows system automatically.

And if all goes wrong (not likely), you can re-install the mbr with windows (as you once did).
Fish in the forums how to do this. To be save, create a boot floppy first, if you don't have a full win recovery CD (but still a floppy drive in the system).[/QUOTE]

Actaully no. I sortof changed my installation plan after the first post. I see it's a bit confusing what I wrote there.

Anyhow, I'll probably have a go at Ubuntu this weekend if I get time. Just one thing, I saw somewhere at a forum this guy claiming that fixmbr didn't work with SP2 installed. Anyone else heard anything about this? I found that hard to belive.

---

### Post by joseftu on 2005-11-15
I had a horrible time, just today, and ended up totally re-installing XP, because fixmbr did not work at all.  Had a good ubuntu installation (first time) but XP would not boot.  In GRUB, when choosing XP, the system would just flash right back to GRUB.  Over and over again.  Tried everything (editing menu.lst as many ways as I could think of), but nothing worked.  Finally resorted to fixmbr to totally wipe out GRUB, but even fixmbr had no effect.  GRUB still loaded.

Should probably start another thread, I know, but I wanted to just throw in that fixmbr apparently does not always wipe out GRUB, contrary to what all my web searches had indicated!

---

### Post by dudus on 2005-11-17
try to remove any other hard drive you have. Leave only the windows HD as primary master and booting in boot sequence.

pop in the winxp cd rom. now get into the recovery console and type fixmbr.

this should do the work.

reboot

---

