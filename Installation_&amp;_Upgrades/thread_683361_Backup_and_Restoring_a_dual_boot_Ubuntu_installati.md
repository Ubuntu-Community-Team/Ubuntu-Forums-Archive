---
title: "Backup and Restoring a dual boot Ubuntu installation."
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by BuntuFreak on 2008-01-30
I have backed up and restored Ubuntu installations a couple of times using Partimage using the SysRescue CD. Works like a charm. But now I'm trying to do something a little different. And given the time I've spent getting my Ubuntu desktop to work just right, I thought I would get some opinions on how I should go about it.

This is how how I went about preparing my desktop. I have a 160 GB drive. I first created a 120 GB partition. Old computer BIOS prevented me from creating anything larger. I installed Windows XP on this partition. I then created a partition with the rest of the disk, around 30 GB (yeah I know 160 GB HD, but I can only see 150 GB total, don't ask, don't care). 

Then I proceeded to install Ubuntu on the 30 GB partition, creating 1GB swap space at the end of the disk. I rebooted and got Grub error 18. Very quickly I learnt about my BIOS not being able to address disks larger than 132 (or is it 137 ?) GB. Solution was to create a "boot" partition at the beginning of the 30 GB and waste it. So I went back, created a 512MB partition, around 29.5 GB partition, and then 1GB partition for swap space at the end and reinstalled Ubuntu. Presto! I now had GRUB dual booting my machine.

So this is my question. I have 4 partions on my disk right now. 120GB (XP), 512MB(boot), 129GB(root) and 1GB(swap). I dunno where GRUB is loaded exactly. My objective is to give more drive space to Ubuntu. So I would like to reduce my XP partition to say 30 GB and give 120 GB to Ubuntu. Instead of reinstalling both OS's, I was thinking of using Norton Ghost to backup my XP installation and Partimage to backup my Ubuntu installation, then repartitioning my drive as 30GB, 512MB, 120GB, 1GB. Then restore XP on my 30GB using Norton Ghost, and Ubuntu on the 120GB using Partimage.

Will this work? Will the MBR, Grub, whatever get installed correctly?  If someone can please set me straight. The Windows install is less of a pain, but having to resintall Ubuntu is going to be royal pain. Any advice deeply appreciated.

---

### Post by Partyboi2 on 2008-01-30
You could use the ubuntu live cd and use gparted (System>Admin>Partition Editor and use the resizing tool to shrink xp and increase ubuntu without having to repartition. If you do not have a ubuntu live cd you can download [gparted live cd]("http://gparted-livecd.tuxfamily.org/")

---

### Post by BuntuFreak on 2008-01-31
Okay, I have used GTParted before. That was when I dual booted a desktop that already had Windows XP on it and I wanted to create partition at the end.

GParted seems a lot like GTParted. Regardless, I understand I can shrink my Windows partition using this tool. But that will create a "hole" in my disk. Can this tool also move the starting points of all remaining partitions to the "left"?

Or maybe I'm missing something. Perhaps you are saying I can simply create a brand new ext3 partition in the "hole" left behind after shrinking the XP partition? Maybe I'm so focused on increasing the size of my Ubuntu partition, I'm not thinking clearly. Please set me straight.

---

### Post by Partyboi2 on 2008-01-31
You should be able to resize from the beginning or the end of a partition with gparted. So you will not need to create another partition

eg. If windows is on the first partition you would shrink the end of it down to what ever size. Then you would increase the size of the next partition from the beginning of that partition to swallow up the free space. If the setup was something like 
Partition 1 =windows
Partition2 = /boot
Partition 3 = /root
Partition 4 = /swap
You could shrink windows down, and move /boot along to the end of the windows partition and move the end of the /boot down so that you end up with the 512mb again for /boot. Then move /root to the end of the /boot partition taking all free space and leaving /swap as it is. So basically moving everything to the left except /swap. Like playing musical chairs.

Remember to back up your important stuff.

---

