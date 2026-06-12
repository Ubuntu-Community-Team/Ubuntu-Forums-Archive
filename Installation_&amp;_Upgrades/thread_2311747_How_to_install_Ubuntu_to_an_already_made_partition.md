---
title: "How to install Ubuntu to an already made partition without wiping the full hard drive"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by Camilo_Morrice on 2016-01-29
I'm new to Ubuntu so sorry for the noob questions.
I'm dual booting Windows, Remix OS 2, and (hopefully) Ubuntu on one hard drive.
I made this hard drive into a couple partitions with each operating system getting partitions for itself.
I want to install Ubuntu onto my already made partition but I can't find the option to and to me it looks like Ubuntu will completely wipe the hard drive for itself.
How can I install Ubuntu onto my already created partition? (it was created in windows if that matter at all)

---

### Post by Dennis N on 2016-01-29
When you reach the page in the Installer titled "Installation Type" select the "Something Else" Option near the bottom. Then on the next page you can select the partition you intend to use for the installation, click on "Change" and fill in a few details on how it is to be used - usually ext4 journaling file system, and mount at /. You probably already have a swap partition, it should be detected during the install and reused.

Good Luck.

---

### Post by Melnik_Hoogland on 2016-01-29
Did you format your Ubuntu partition as ext2, ext3, or ext4, or did you just let windows pick the format? If you didn't format it as ext2/3/4, you should (gparted, which comes with the Ubuntu CD, can do this, but formatting a partition will delete ALL data on that partition so make sure you have anything you want to keep on that partition backed up). Once this is done, boot Ubuntu, run the installer, and proceed until it asks you whether you want it to erase the hard drive. There should be a "something else" option; select that one. On the next screen, select the partition you created, double-click on it, and make sure it's being used as an "ext2 file system" if you formatted the partition as ext2 or an "ext3/4 journalling file system" if you made it ext3/4, then set the mount point to "/". Make sure the "device for boot loader installation" is set to /dev/sda, not /dev/sda with a number after it, then click on "install now." It should install to the partition you made.

---

### Post by petko-krasimirov99 on 2016-01-30
If this partition is ex3/ex4 you don't have to format.  Just click on something else and click on mounting point and write / 
Advise: On the other part of you hard drive you can mount as /home and in that way when you reinstall your OS you can just format / not home /home
Good luck!  I hope I help!

---

### Post by Bucky Ball on 2016-01-30
*Thread moved to **Installation & Upgrades**.*

If the partition was created with Windows, which the OP clearly states it was in the first post, it will not be EXT* anything. Don't bother creating any partition with Windows for your Ubuntu install. Leave free space, use 'Something Else' when you get to the partitioning section of the install, create the partition using the free space and make its mountpoint /. That is a default you can select in there. 

What about /swap? If you already have one, mark it to 'Use'. This will save you having to create another /swap and having two (which you don't want or need). If you don't have one, create one, make it 2Gb and put it at the end.

This can all be done in the 'Something Else' section of the install.

---

