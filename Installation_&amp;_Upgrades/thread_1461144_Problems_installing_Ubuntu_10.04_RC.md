---
title: "Problems installing Ubuntu 10.04 RC"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by fterh on 2010-04-23
I booted from the CD, chose to install (without trying), and when it comes to the "select a partition" page I chose the first option (install alongside Windows loader).

After the installation has completed, when I rebooted, there wasn't an option to choose between Windows & Ubuntu. In Windows, I couldn't find the Ubuntu installation anywhere, although I think there was one new partition (without drive letters).

I tried again, this time specifying the partition I've made (in Windows) specially for Ubuntu. It keeps telling me "no root system found", and I just couldn't get it to install. I tried deleting the partition and making a new one out of the free space (within Ubuntu) but it keeps giving me the "no root system found" error.

Hence I've decided to install using Wubi (in Windows) in the partition I made. 

But just curious, where did I go wrong?

Update: Even Wubi doesn't work. After installation has completed I can choose between Windows 7 and Ubuntu during startup. But when I choose Ubuntu, an error flashes (too quickly for me to see what it says) and I'm brought to a "choose loader" screen. Both loaders are Windows 7, and choosing either one brings me back to the "Windows 7 or Ubuntu" screen.

---

### Post by oldfred on 2010-04-23
You cannot create partitions with windows that Ubuntu will use. You can create free space. I always create partitions in advance and use the manual install, but then I have to specify which partition is / (root) and /home, it seems to find my swap automatically. 

The other choices are along side(you have to tell it to move existing space), free space or full disk, but it should auto create just root & swap. 

Perhaps your existing system has used all 4 primary partitions so the system cannot create any more? Windows 7 for new installs uses 2, many systems have a recovery partition and sometimes another partition, so they use all 4 and make it difficult to allow anything but windows on the system.

---

### Post by fterh on 2010-04-23
> **oldfred said:**
> You cannot create partitions with windows that Ubuntu will use. You can create free space. I always create partitions in advance and use the manual install, but then I have to specify which partition is / (root) and /home, it seems to find my swap automatically. 

The other choices are along side(you have to tell it to move existing space), free space or full disk, but it should auto create just root & swap. 

Perhaps your existing system has used all 4 primary partitions so the system cannot create any more? Windows 7 for new installs uses 2, many systems have a recovery partition and sometimes another partition, so they use all 4 and make it difficult to allow anything but windows on the system.

Okay I've since created free space, used Ubuntu to create swap and ext4 (/ mount) and installed Ubuntu. But still I'm not receiving the choose OS screen upon startup. I have 2 hard drives, Windows is installed on HDD B while Ubuntu HDD A. 

Does the swap and and ext4 have to be primary? Perhaps I read wrongly, but the documentation states that they can be logical.

[IMG]http://i42.tinypic.com/vfdtnc.png[/IMG]

Note: I have no idea why the mount is not "/", I specified "/" during installation. I'm on LiveCD, fyi.

---

### Post by oldfred on 2010-04-23
No linux partitions have to be primary. Windows has to boot from a primary with the boot flag. Some BIOS assume windows and want to see a boot flag on a primary to let you boot so I always put a boot flag on a primary partition.

If you format sda6 to either ext3 or ext4 and choose that partition as / (not the label) it should work. Since you have good sized drives I might make a separate /home then your root only has to be 10-20GB. But it looks like at least for now most of your data will be in the NTFS partitions. Swap only needs to be as large as your RAM. 

I only had root & swap with a shared FAT (now NTFS) partition for data between XP and Ubuntu for three years. With Karmic I reorganized & now I am in XP so little most of my data is in /data which is ext3. My root is 5-6GB, my /home is 1GB,  and  all my data is in other partitions linked into home.

---

### Post by fterh on 2010-04-24
The thing is, after Ubuntu installation, my system launches RIGHT INTO Windows! :confused:

---

### Post by oldfred on 2010-04-24
There is an adanced button after the partition screen in the install that lets you choose which drive to install grub to. Grub probalby installed to a different drive and you still have the windows boot loader in the drive BIOS has as primary master or first boot drive.

Look in BIOS and change your boot drive.

If you want to see what is installed where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

I alway run script before and after any major system changes so I know where things are and save a record.

---

### Post by P4man on 2010-04-24
> **oldfred said:**
> 
Look in BIOS and change your boot drive.

that.

As for / not being /, that is because you are on the livecd, which has its own filesystem, and its own /. gparted looks okay to me, even if a bit messy.

---

### Post by fterh on 2010-04-24
> **oldfred said:**
> 
Look in BIOS and change your boot drive.


Thanks, worked perfectly :D

---

