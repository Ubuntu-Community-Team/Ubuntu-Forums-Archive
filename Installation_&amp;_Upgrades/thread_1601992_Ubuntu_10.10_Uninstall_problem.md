---
title: "Ubuntu 10.10 Uninstall problem"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by Amit_Olkar on 2010-10-20
I downloaded the Ubuntu 10.10 desktop iso and transferred it to a USB flash drive. Installed via WUBI using the same on Windows 7. At installation time, I assigned 30GB space on a a partition. After installation and logging in to Ubuntu, the updater ran and asked for a reboot. After the reboot there was some error and I kept getting grub screen. I rebooted in Windows and ran the uninstaller. 
It uninstalled Ubuntu but the drive doesn't report the same 30GB space as free. What can be done to solve this problem ?

---

### Post by dusan.saiko on 2010-10-20
Ubuntu just used free space, created linux partition and formated it using ext4 filesystem. Ubuntu uninstaller does not destroy the linux partition, which Windows does not understand, so it probably reports it as unknown used space. 

So if you are sure you do not want anything from the Linux partition anymore and if you are sure you are looking at the right one, you can delete the partition under Disk Management in Windows and create a new one, which Windows can read.

Note: actually be quite careful with this. I have no experience with Wubi so do not know if it really created it's own partition, but seems like that from your post.

---

### Post by Amit_Olkar on 2010-10-20
The problem is that I have some data on the rest of the partition, for which I don't have space to back up at the moment. And in the past when I uninstalled Ubuntu ( 9.04 on Vista ) it did not have this problem. It reported all the space properly, and I was able to use it.

As far as the Linux partition goes, I do want to install Ubuntu back on to it, but through WUBI, and the WUBI doesn't show that space as a Linux partition, nor does the Disk Manager in Windows.

---

### Post by dusan.saiko on 2010-10-20
So is not there any single file (or possibly directory) into which Wubi would install the system ?

---

### Post by Amit_Olkar on 2010-10-20
No. All of it is gone. I have attached the screenshots for your reference.

---

### Post by dusan.saiko on 2010-10-20
Are you displaying even hidden files ?

---

### Post by Amit_Olkar on 2010-10-20
Yes. Everything is being shown.

---

