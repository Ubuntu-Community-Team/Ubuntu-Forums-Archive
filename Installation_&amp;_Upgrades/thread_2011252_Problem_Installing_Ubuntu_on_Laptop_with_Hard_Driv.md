---
title: "Problem Installing Ubuntu on Laptop with Hard Drive Accelaration Cache"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by vinodkhare on 2012-06-26
I have an HP dm4 3170se laptop with 'hard drive acceleration cache'. When trying to install ubuntu 12.04, the installer does not see any of the partitions. 

Any clue what could be wrong?

---

### Post by dino99 on 2012-06-27
is gparted seeing these partitions ?

---

### Post by black veils on 2012-06-27
is Windows on that computer? if yes, go to the disk management utility and look at the disk layout. under the header **type**, does it say **basic** or **dynamic**?

the application looks like this: [http://citrixblogger.files.wordpress.com/2008/10/disk-management-tool.jpg](http://citrixblogger.files.wordpress.com/2008/10/disk-management-tool.jpg)

---

### Post by vinodkhare on 2012-06-27
The disk type is 'basic'.

---

### Post by vinodkhare on 2012-06-27
Yes, gparted is able to see the partitions but shows an error icon (!).

---

### Post by black veils on 2012-06-28
Basic is good.

Disk Utility is your next stop then, to see if your hard drive  is bad.

---

### Post by vinodkhare on 2012-06-28
The hard drive seems okay. I just got this laptop from the store this weekend. It still has the default partitions and works without a problem on windows.

I shrunk the default windows partition using the disk utility to make space for linux but the installer fails to see any partitions on the disk.

---

### Post by black veils on 2012-06-28
can you do what it says in the first post here: [http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)


did you do an md5sum check of the .iso you downloaded, before putting it to cd/usb? and how did you create your medium? cd requires the slowest burning speed possible: 1x 2x 3x


Edit:

maybe this will be of use (specifically the last post) [http://askubuntu.com/questions/99038/why-the-ubuntu-installer-does-not-detect-the-hard-drive-during-installation](http://askubuntu.com/questions/99038/why-the-ubuntu-installer-does-not-detect-the-hard-drive-during-installation)

---

### Post by vinodkhare on 2012-07-04
I managed to solve this. The 'hard drive accelaration cache' is a small SSD drive that is setup as a RAID device along with the regular hard disk in windows. This was preventing the Ubuntu installer from seeing the disk. I disabled accelaration under Windows and was then able to install Ubuntu in the usual way.

---

