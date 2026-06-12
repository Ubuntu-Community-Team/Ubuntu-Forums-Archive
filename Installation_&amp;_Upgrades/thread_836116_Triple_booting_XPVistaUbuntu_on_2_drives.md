---
title: "Triple booting XP/Vista/Ubuntu on 2 drives"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by dog.tired on 2008-06-21
I am wanting to make 100% sure of the installation procedure before I start, so I dont mess up my current config! 

I have just set up a dual boot using clean installs of xp and vista and am in the process of installing software/updates, so I dont want to mess it up.

Current config:

Drive 1: C: (100gb) D: (220GB)
Drive 2: E: (320gb)           - both Samsubg 320gb SATA drives

C: XP - with EASYBCD installed controlling boot (Boot directory and bootmgr file transfered from vista drive and used to set up boot manager)

D: XP DATA - partition of C:

E: Vista

I am thinking that I want to install Ubuntu on the Vista drive and have the EASYBCD prog recognise it as an option at bootup. Could you please give me a basic run through of the best/safest way to achieve this?

Thanks a lot. :KS

---

### Post by Pumalite on 2008-06-21
You nee to allocate space for Ubuntu with the Vista partitioner.

---

### Post by Computer Guru on 2008-06-21
See the step-by-step EasyBCD/Ubuntu pictorial at [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by dog.tired on 2008-06-22
I managed to mess everything up and have had to reinstall vista again, but Ive finally got it worked out properly.

I disconnected the XP drive when first installing, (as I thought it might complicate matters, or get damaged in the install),  which just added to the confusion! I realised it messed up GRUB, so I reconnected it.

I basically followed the given tutorial apart from a few things. I used vista to partition the E: drive and left the new partition unallocated, then in the Ubuntu installer I selected "guided-next continuous" then did the whole /dev/sdb2 thing.

I now have Ubuntu 7.10 on my pc. (I had an old disc lying around). I am downloading the 8.04 so another format and install is in order I suppose!



_**EXTRA QUESTIONS:**_

I have a BELKIN FD57050 v2 wireless adapter, I have seen quite a few threads describing problems with these, should I just not even try?

Also, I am using a Nvidia 7500LE graphics card with a couple of monitors, but when I try to add the DVI monitor Ubuntu loads to a black screen. (I couldnt get it to install without removing the 2nd monitor either!)

Thanks

---

### Post by bigpoppa on 2008-06-23
hey guys i have a similar problem... i have a 640gb hdd and i already have separate partitions for xp and vista with vista doing the boot manager thingy and 2 other partitions for files and games.. 

i installed ubuntu on a blank partition.

at the end of the ubuntu 8.04 installation GRUB dont recognize XP as one of my OS's (only vista) so i decided to skip it and hoped that maybe the vista boot manager will recognize ubuntu on the other hand, it didnt.


any tips?

p.s. sorry i dont wanna make a thread of my own regarding this, i apologize mr. thread starter.

---

### Post by Pumalite on 2008-06-23
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by bigpoppa on 2008-06-23
pumalite?

need help guys :(

---

### Post by Pumalite on 2008-06-23
Boot your Live CD and post first:
sudo fdisk -lu

---

