---
title: "Installed Ubuntu on newly shipped Dell Inspirion Desktop. Can't boot either OS"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by vikasb on 2010-09-26
Hello Experts!

I do not know if I can salvage things here.

I was happy to boot to my newly shipped Dell Inspirion desktop with Win 7 and the first thing I did was download ubuntu from the wretched IE. I later installed Ubuntu from the burned CD. The version is 10.04. On restart, I got a boot menu with Ubuntu on top and Win 7 on bottom as expected. I used Ubuntu for the last 2 days without need to use Win 7. But then my friend wanted a file which I had saved in Win 7 and I therefore booted to Win 7 for retrieving that file for my friend. Then Windows (First time windows boot after Ubuntu installation) tells me there was some issue and it needs to recover. I clicked yes, It did something for few minutes (I do not remem the messsage, sorry :(.. I expected Window to discover Ubuntu got installed and therefore save it for the user.) Thereafter, Windows booted correctly, I logged into my account sent that file to myfriend via email and then wanted to come back to Ubuntu. I restarted to login to Ubutu. On restart, I am expecting the boot options of Ubuntu first and Win 7 later, BUT to my shock, I get only a black screen, saying it doesn't have any boot information. 

I booted to the live CD. Here is sudo fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        1302    10360832    7  HPFS/NTFS
/dev/sda3            1302       40964   318582208    7  HPFS/NTFS
/dev/sda4           40964       77826   296090625    5  Extended
/dev/sda5           40964       76360   284318720   83  Linux
/dev/sda6           76360       77826    11770880   82  Linux swap / Solaris

I want to recover both Win 7 (As I did not create a recovery disk) and Ubuntu because there is 2 days of work on my Ubuntu. 

Please help. Its greatly appreciaited. 

Thank you
Vikas

---

### Post by grahammechanical on 2010-09-26
First, Linux (Ubuntu) needs to live with MS Windows, so a lot of effort is put into making it possible to install Linux along side Windows. But, MS Windows does not need to live with Linux. So, no effort is made by the MS developers to allow the two Operating systems to cooperate together.

Second, From Ubuntu you can read and write to the Windows partitions but not the other way around. so you could have retrieved that file from within the Ubuntu OS.

Third, I am not an expert, so I can only point you in the right direction. You need (in my opinion) to get some information about GRUB2 (Grand Universal Boot Loader) and how to fix it when it is broken. There are some posts in this forum that explain how to execute a command to update GRUB. That is what you must look for.

Fourth, Can you confirm that you cannot boot into Windows. Or is it only Ubuntu that you cannot boot into? This point is not clear. 

Fifth, The live CD will let you access your files. Perhaps you can email them somewhere as a form of back up.

Sixth, the two installations are still on the hard disc. It is only the Master Boot Record (MBR) and the boot loader (Grub) that are somehow messed up.

regards.

---

