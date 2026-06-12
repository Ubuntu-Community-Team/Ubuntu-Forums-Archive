---
title: "How do i dual boot vista and ubuntu on 2 seperate HDDs?"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by samn122 on 2010-08-25
I have Vista installed a 500 gb and recently added a 320 gb hard drive. How do I install ubuntu on to the 320 gb HDD and be able to dual boot the 2 operating systems? Also how do I keep myself from getting the **symbol** 'grub_puts' **not found **error when updating to 10.4?:(

---

### Post by roy913 on 2010-08-26
> How do I install ubuntu on to the 320 gb HDD and be able to dual boot the 2 operating systems?
When one installs ubuntu on a machine which windows already exists, ubuntu will automatically add the required lines into grub to dual boot the windows OS. Let me know if this is not true in your case.

> Also how do I keep myself from getting the symbol 'grub_puts' not found error when updating to 10.4?
have you tried this:
[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html]("http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html")

---

### Post by oldfred on 2010-08-26
Some good info on installing on two drives. I do like to keep each system's boot loader on the same drive so each drive can be booted from BIOS if need be. But grub2 will find the windows install and let you boot either system.

If you are using both Windows & Ubuntu it is worthwhile to also create a shared data partition NTFS for any data you want available for both systems.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Install Screens shown with advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png]("http://members.iinet.net.au/%7Eherman546/p24/022f.png")


Partitioning basics with some info on /data older but still valid by bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by oldfred on 2010-08-26
Please do not post duplicate threads. We all are volunteers and do not want to create duplicate responses.

See
[http://ubuntuforums.org/showthread.php?t=1561198](http://ubuntuforums.org/showthread.php?t=1561198)

---

### Post by samn122 on 2010-08-26
I'm sorry. I posted my question to the wrong section thought of re-posting it here.

---

### Post by samn122 on 2010-08-26
Thanks. I successfully dual booted the 2 systems. The problem im having now is preventing myself from getting the "symbol 'grub_puts' not found" error when updating to 10.4. Before posting, I had tried to install ubuntu and update it by myself. After installing it I updated it to 10.4. After I was done updating, I restarted my computer and found that GRUB would not load but instead  gave me a  "symbol 'grub_puts' not found" and a "grub rescue>" so I couldn't choose which operating systems to load. Because of that i had to do a clean install of Ubuntu 9.1 again which somehow fixed GRUB and I was able to dual boot again. Now im trying to find a way of updating to 10.4 without screwing GRUB up which i did.

---

