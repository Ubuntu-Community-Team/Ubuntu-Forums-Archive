---
title: "Dual Boot Ubuntu w/ XP"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by Nalos Surith on 2005-07-10
Currently I am trying to dual boot ubuntu with windows xp( I have much data on this which I do not want to loose). 

On one hard drive I already have 2 NTFS Partitions, 1 FAT32 and 1 EXT3. To make those partitions I have used Partion Magic, also I have Boot Magic installed.

I am wondering since there is an ext 3 partition already allocated w/ 10GB's will ubuntu install it on that partition without destrorying the windows partitions through the default installation, or will I have to go through the expert installation to do so. If so can some one walk me through the default or the expert on how to install ubuntu 5.04 properly.

Thank You,
[EMAIL=nalos.surith@gmail.com]Nalos Surith[/EMAIL]

---

### Post by Leif on 2005-07-10
Don't worry, you can use the normal installation. Just make sure that you do not accept if it offers to wipe the entire harddisk. Since you've formatted the space you want to install it to, you'll probably have to delete that first (you can do this with the installer), as ubuntu will need to split that into several partitions and will perform its own formatting. So basically, delete the existing ext3 partition, then choose for ubuntu to automatically partition the empty space. Before committing to anything, you should be able to see that your windows partitions are still there, plus several new ones made by ubuntu.

---

### Post by Nalos Surith on 2005-07-10
Much thanks dude, though I had to figure out some settings my self during the installation. The one big thing that I had to do was to go on to windows xp and set boot magic to start up the ext3 (now reiserFS) partition since i didn't install grub. =)

But over all everything seems too look good.

---

### Post by Nalos Surith on 2005-07-10
... It seems to start to start up then goes to "Preparing machine to load 'Ubuntu'"....gonna reboot to see if it works ok this time....

Edit: It just seems to go to the same thing....no change ¬.¬

---

