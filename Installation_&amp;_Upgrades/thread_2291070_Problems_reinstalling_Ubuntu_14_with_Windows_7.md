---
title: "Problems reinstalling Ubuntu 14 with Windows 7"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by Kwame_Danielson on 2015-08-17
I have a laptop with Windows 7 preinstalled on it. I wanted to try a Ubuntu on it with a dual boot. I am beginner with Linux but having rooted various phones, I understand the importance of research and following instructions. I created a bootable USB with Ubuntu 14.04.3 on it and tested it. It worked on various computer and I even installed it on a netbook I no longer use, deleting Windows on that machine in the process. I was ready to try to install the dual boot. The installer read that I had Windows 7 on the machine and I chose to install ubuntu inside of Windows. Finished the install and rebooted the computer. It gave me the option of dual boot. Booting into Windows worked fine. Booting into Ubuntu would just give me a blank black screen. I let it sit but no changes. I restarted and tried again. Same thing. So I thought that I would try to uninstall and reinstall. Uninstalled from inside Windows and that went fine. However, now, the Ubuntu install no longer recognizes that I have any operating system on my machine and wants me to erase disk to install Ubuntu. What did I do wrong or how do I figure out what I did wrong? Windows 7 still works fine on the machine. Live Ubuntu works fine off of the same USB installer stick. Thanks for any advice. As a beginner, I completely out of my depth at this point.

---

### Post by TheFu on 2015-08-17
Could I convince you to try running Ubuntu inside a virtual machine first?  It is much easier, much less risky, provided the system has enough CPU and RAM.  Any Core2Duo or faster CPU with 3+ GB of RAM is enough to test it out.  Plus with a VM, you don't have to repartition the HDD, which is a risky thing - especially for people who don't do it all the time.  A small mistake and everything on the computer can be gone.

Running inside a VM makes things easier.  15G of disk and no worries about network drivers/wifi. The only downside is graphics performance. It isn't bad and only matters for gamers.  For normal users trying to get things done in a business environment, the graphics performance of virtualbox on Windows is pretty good.

So - if you do go the dual boot method, please, please, please make a perfect, know-you-can-restore backup AND TEST IT!!!!!!  Before doing anything else.

Ok - since you've already gone passed the point ... try boot-repair first. my signature has a link.

---

### Post by grahammechanical on 2015-08-17
How did you uninstall Ubuntu from inside Windows? Did you simply delete the Ubuntu patitions? Or did you install Ubuntu inside Windows using wubi.exe in the first place?

If the motherboard has a BIOS boot system then there is a 4 primary partition limit on the hard drive of that machine. If you did a true dual boot and not a wubi.exe install then the installer might have created a primary partition which it then converted into a special primary partition called an Extended partition. The installer may have then installed Ubuntu inot a logical partition inside the Extended partition and another logical partition being used as a swap partition.

The point being that the first install may have used up the 4 primary partitions allowed and for that reason can no longer offer to install alongside. It can only offer to install by erazing what is there. Load Windows and use a Windows utility to look at the partiiton layout and then take a screen shot and post the image here so that we can see for ourselves the partition layout.

Regards.

---

### Post by TheFu on 2015-08-17
For partition data, I would much prefer he boot any Linux and run **sudo parted -l** and **lsblk** to get a more complete picture than current Windows disk manager provides.  Please and thank you.

---

