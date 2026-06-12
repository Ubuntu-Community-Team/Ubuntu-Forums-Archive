---
title: "[SOLVED] Removing Fedora 8 from a 7.04 dual boot system"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by armalite1969 on 2008-01-06
I have 7.04 and Fedora 8 running on one drive and Win XP on another drive.  I want to uninstall Fedora 8 without messing up 7.04.  What is the safest way to do this?

---

### Post by ryanVickers on 2008-01-06
if the grub is NOT in the fedora core, then you can just format it...

if the grub IS on the fedora partition, download a copy of Super Grub Tool first to restore it after you've formatted.

---

### Post by armalite1969 on 2008-01-06
Thanks for the response, I am fairly new to linux, how will I tell if I am in the Fedora grub or not?

---

### Post by armalite1969 on 2008-01-06
Additional info,

I first had Ubuntu on the drive, I then installed Fedora.  When the system boots, it has the Fedora splash screen which gives me 10 seconds to press a key.  If I don't do anything, it boots to Fedora.  If I hit a key, It then goes to a different screen allowing me to select Fedora 8, Ubuntu, or WIndows XP.

---

### Post by logos34 on 2008-01-06
Then it's obviosuly using the Fedora grub.  (rule: grub corresponds to the last intalled linux)

You don't need the Super Grub Disk or any live cd for that matter (although SGD is something you should probably have on hand)

Just boot into feisty and write the ubuntu grub to the mbr:

**sudo grub-install /dev/sda**  (--> replace sda with whatever your ubuntu disk is).

Thne delete fedora using Gparted in ubuntu (sudo gparted)

---

### Post by armalite1969 on 2008-01-06
logos34, thanks for you help.  Did what you said and it worked.  I have 30 or so gigs of free space now.  Is it safe to resize my ubuntu partition to utilize the free space freed up from Fedora?  Can I use gparted for this?

---

### Post by logos34 on 2008-01-06
> **armalite1969 said:**
> logos34, thanks for you help.  Did what you said and it worked.  I have 30 or so gigs of free space now.  Is it safe to resize my ubuntu partition to utilize the free space freed up from Fedora?  Can I use gparted for this?

You will need to use the live cd to resize root partition (root cannot be mounted).  yep, use gparted.

ADD: although swap may be between them.  dunno.  Post your 

**sudo fdisk -l**

---

### Post by ryanVickers on 2008-01-06
gparted can expand partitions to the right, but not to the left (unless its under certain circumstances)

the live CD (of gprated) apparently can do this, but not the normal install.  things that say they can me "moved" can do this, but not all filesystems

---

### Post by logos34 on 2008-01-06
> **ryanVickers said:**
> gparted can expand partitions to the right, but not to the left (unless its under certain circumstances)

the live CD (of gprated) apparently can do this, but not the normal install.

correct. 

But that may not be an issue because he probably has the freed space on right (fdisk will show in a minute)

---

### Post by armalite1969 on 2008-01-06
in gparted the free space is on the left.

---

### Post by ryanVickers on 2008-01-06
well that could be a problem... you may have to use the gparted live CD but since that doesn't work anyways, would it be possible to make a partition there, move the entire other partition contents, and then delete the one on the right, and then expand it to fill the whole "old space" plus the new 3oGb? (thats what I would do if theres room :D)

---

### Post by armalite1969 on 2008-01-06
I don't mind doing that, I just don't know how to exactly.  What would happen if I resize my ubuntu partition into the unallocated space?  I attached a screenshot of gparted.

---

### Post by logos34 on 2008-01-06
so the space is on the left.  (hah, wouldn't ya know. make a liar of me)

> **armalite1969 said:**
> I don't mind doing that, I just don't know how to exactly.  What would happen if I resize my ubuntu partition into the unallocated space?  I attached a screenshot of gparted.

The latest Gparted live cd will be able to expand root left to front of disk no prob.  But when resizing to left it takes a looong time (hours), even if there's just a few gigs...it has to copy and move all the files.

---

### Post by ryanVickers on 2008-01-06
if you are actually able to boot the live CD and resize it, I would say go ahead, but since it doesn't work for me, I would create a new partition in the empty space, move everything, delete the old one, and then expand the new one to fill the drive (except the swap ;))

---

### Post by armalite1969 on 2008-01-06
So the live gparted is on the live 7.04 cd?  All I need to do is boot to the 7.04 CD (this is a cd i created myself off the net) and run the utility?

---

### Post by ryanVickers on 2008-01-06
no, the gparted live CD is separate and more powerful than the gparted that comes with ubuntu

---

### Post by armalite1969 on 2008-01-06
Sorry for bugging with all the questions, where is the best place for getting the live gparted CD?

---

### Post by logos34 on 2008-01-06
> **ryanVickers said:**
> if you are actually able to boot the live CD and resize it, I would say go ahead, but since it doesn't work for me.

apparently there's a misunderstanding...gparted on the UBUNTU live cd cannot do it (it's an old version-- 0.2.6 or something).

You need to use the **Gparted** Live cd. (0.3.4)

---

### Post by logos34 on 2008-01-06
> **armalite1969 said:**
> Sorry for bugging with all the questions, where is the best place for getting the live gparted CD?

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by armalite1969 on 2008-01-06
I made the Gparted CD 3.4.  All I have to do is boot to it and resize the partition?

---

### Post by ryanVickers on 2008-01-06
yup! :D

(assuming it actually boots... mine never did...)

---

### Post by armalite1969 on 2008-01-06
cool, will do and i will let you all know how it went.  Thanks again for the assistance.

---

### Post by armalite1969 on 2008-01-07
Seven hours later and all seems good.  THanks for all the help!!!!

---

