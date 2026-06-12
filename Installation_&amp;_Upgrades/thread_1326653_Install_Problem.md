---
title: "Install Problem"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by gallicbear on 2009-11-14
Hi there,
Downloaded 9.10 with the intention of installing it in an empty partition, to run alongside with XP. However, the options given are baffling me. 
Either to install alongside Windows inside the same partition, 
or 
to do a full installation. 
When I click on that, it's asking me to reboot. 
Can it only do the job I want by rebooting?

---

### Post by darkod on 2009-11-14
Personally I always select Manual Partitioning when asked about the location. Gives you most control.
What you call empty partition might be empty but if it created partition Ubuntu will not consider it. If you are sure you don't need it, go into manual partitioning, delete the partition, when it's empty SPACE create at least / (root) ext4 partition and 2GB swap partition. Creating ext4 /home partition is optional. That's all you need for a start.

I don't trust the automated installs, after all it's a machine. :)

PS. There is difference between empty space and empty partition. If a partition exists, even without data, ubuntu has to delete it and create new one. You can delete it manually and create the new one also. Safe choice against something going wrong.

---

### Post by Revolutionary101 on 2009-11-14
The only way to install it on that empty partition is to reboot your computer. When the installer appears after you reboot it should ask you what partition you want the install to be on. Then you just select the empty partition and it will start installing.

---

### Post by gallicbear on 2009-11-14
Thank you for your reply. I rebooted and used the CD to install. 
It plowed ahead without giving me any options on WHERE to install. By the time it installed the clock and started connecting to the network, I stopped it to avoid problems in my Windows XP boot records. My intention is to keep XP and to familiarize me with Ubuntu. 
I do have an empty partition already, with approx. 50 GB of space.
Don't even know where the install placed files. Should be more user friendly in my estimation. 
Any ideas? Would appreciate to hear from someone on how to make sure it installs in the partition of my choice.

---

### Post by dhavalbbhatt on 2009-11-14
> **gallicbear said:**
> Thank you for your reply. I rebooted and used the CD to install. 
It plowed ahead without giving me any options on WHERE to install. By the time it installed the clock and started connecting to the network, I stopped it to avoid problems in my Windows XP boot records. My intention is to keep XP and to familiarize me with Ubuntu. 
I do have an empty partition already, with approx. 50 GB of space.
Don't even know where the install placed files. Should be more user friendly in my estimation. 
Any ideas? Would appreciate to hear from someone on how to make sure it installs in the partition of my choice.

Try using the alternate CD to install Ubuntu 9.10. It is not GUI based, rather has the CLI, but don't fret, there is nothing to worry about and you can get the job done just as easy.

---

### Post by gallicbear on 2009-11-14
Thank you all for your help. I used my partition manager and saw that Ubuntu had created its own partition. Which was okay. I re-initiated the install. Everything runs now.

---

### Post by presence1960 on 2009-11-14
you do not have to remove an unused partition to install Ubuntu onto it. Select manual at the partitioner window and select that partition. Then set "use as" (filesystem) to the filesystem you want to use, tick the format box and set mountpoint to / from the drop down box.

If you do it this way it is wise to create a swap partition also.

---

