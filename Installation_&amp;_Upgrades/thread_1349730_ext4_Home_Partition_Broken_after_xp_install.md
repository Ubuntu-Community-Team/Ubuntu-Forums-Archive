---
title: "ext4 Home Partition Broken after xp install"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Pelonchas on 2009-12-08
Hi, yes i know what you are thinking. "Why did i install xp in my ubuntu box!!!".  I have a dual-bot vista-ubuntu box.. the main reason i keep windows is because of some games i am not able to run in Linux (or they run pretty slow). So Vista takes a lot of space, i decided to try an xp install in a free space i have after my ubuntu home partition. I boot with the ubuntu live cd, get my grub back. Then when i was loggin into ubuntu, it coundt reach the xplash thing, it could not mount home and the new xp partition. So i fixed winxp entry in fstab, and home was the same,  i did not have to changed, but well, i switch /dev/sda6 for my uuid home id to see if something else happens. Nothing i get the same thing. From there( terminal) i can mount the partition but my home has some files about encrypting (i did not agree about encrypting my home in the install). From the live cd, i can not mount it i get the "wrong fs type, bad option ....".
My ext4 root partition is fine, it can be mounted. Home is the only one in trouble.
From live cd, i fsck the home partition, and it get me a lot of bad counters, i went wrint y y y y all over the process, it finished ok.

Nothing...


The worst thing is i did not backedup my home info because it was like a simple os install.

Any ideas??

PD. Sorry about my english. Help me out, i ll give you a free tour whenever you come to Cancun :D.

---

### Post by darkod on 2009-12-08
Can you post the fdisk output or a Gparted screenshot? Much easier to see the disk situation like that.
sudo fdisk -l

---

