---
title: "How to install Grub on its own partition, rather than on the MBR?"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by webster922 on 2009-12-03
I am going to install Ubuntu 9.10 a second time (the first time Grub ruined the Windows 7 bootloader) and use EasyBCD. In order to use EasyBCD I have to install Grub on its own partition.

Instructions are here but are outdated. Or does this guide still apply to 9.10?
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Please help me install Grub on its own partition as Windows 7 writes over it and it becomes corrupt. Thanks in advance.

---

### Post by webster922 on 2009-12-04
For EasyBCD to see Ubuntu, "you must install GRUB to the **bootsector** of your Linux partition, not the MBR." Please help.
 
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) (Ubuntu specific, just need help applying this guide to Ubuntu 9.10 as it is outdated)
 
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux) (Linux, not Ubuntu specific)

---

### Post by misterbk on 2009-12-04
I'm working on something similar...  I've always installed Linux this way, but I think I may have been side-stepping your problem by installing it to a completely separate hard drive.

It seems like the steps in there should still apply just fine...  I haven't tried it myself.  Just see if you can follow the instructions with the new installer.  

The key point to follow is to make sure you have, at some point, told Grub to install to a **partition** instead of a **drive**. (i.e. "/dev/sda2" is good, but "/dev/sda" is bad.)

---

### Post by gabo.cr on 2009-12-04
At Ubuntu installation you need to select "Manual Partitioning"
You would have to specify the other partitions that Ubuntu needs.
You need to choose the partition where you want Ubuntu and then create the rest:

Partition - Size   -  Type
/boot   -  100MB  -   Ext2
/home   -  (GB ?)  -  ReiserFS  
swap    -  (it depends on the size of the HD)

I hope that answered the question.

---

### Post by webster922 on 2009-12-04
On previous installs, I have just used the option 'Install to largest free space'. I make an unformatted partition and it just installs Ubuntu there. But I have looked at the Manual Install (labeled as advanced) option.
 
The problem is that it gives me too many options, the main one being mounting point. The choices are /, /usr, /root, /home, etc. Which one should I choose that will result in Grub installation on the bootsector?

---

### Post by gabo.cr on 2009-12-04
*/boot *is the one you need for Grub, you can give 100MB to it and the Ubuntu installation will do the rest.
But remember that you need to specify the other partitions that Ubuntu needs, such as /home and /swap. Those are the most basic for a manual installation.
;)

---

### Post by louieb on 2009-12-04
> **webster922 said:**
> .. use EasyBCD. 
Instructions are here but are outdated. Or does this guide still apply to 9.10?
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Please help me install Grub on its own partition as Windows 7 writes over it and it becomes corrupt. Thanks in advance.

The instructions are still valid. - When you get to the install summary page you will see the **advanced button** - press it.  There you can tell the installer to put GRUB code in the boot sector of the / root partition. Grub will complain it wants the MBR  - just tell it tough - put it in the boot sector of the / (root) partition.     

BTW: you don't need a separate /boot partition  for EasyBCD  to work.

---

### Post by webster922 on 2009-12-04
To clarify (I don't want to factory restore a second time), I go to the manual install which is the last option. There I will choose to format Ubuntu as ext3 and mount at /boot?

---

### Post by louieb on 2009-12-05
> **webster922 said:**
> . The choices are /, /usr, /root, /home, etc. Which one should I choose that will result in Grub installation on the bootsector?

Whatever you choose here has nothing to do with GRUB being put in the MBR or the boot sector. 

The thing you have to remember is GRUB has two (2) parts.  part1's only function is to load GRUB part2. part1 can go in the MBR or the boot sector of a partition. 

 > When you get to the install summary page you will see the **advanced button** - press it. There you can tell the installer to put GRUB part1 code in the boot sector of the / root partition. Grub will complain it wants the MBR - just tell it tough - put it in the boot sector of the / (root) partition.

part2 of GRUB is found in /boot/GRUB.  It does not matter if /boot is a part of the / (root) partition or in a partition by itself.  

> There I will choose to format Ubuntu as ext3 and mount at /boot? 	 

Again this has nothing to do with part1 of GRUB being put in the MBR or the boot sector.

---

### Post by darkod on 2009-12-05
Just to add to what louieb said.
Since you decided to do things the unusual way, putting grub2 on a partition and chainloading in windows, you need to get some basic info about how linux names the drives straight.
/dev/sda or /dev/sdb are devices, the whole hard drive as device. If it has a number /dev/sda1, /dev/sda5 and like, it's a particular partition on that drive.
When installing ubuntu, on the last screen before clicking Install there is button Advanced. That will open advanced settings which include control where grub2 is installed. That way you can control and put grub2 on any partition you want. If you select /dev/sda it will be the MBR of disk sda, if you select /dev/sda1 it will be the first partition on disk sda, etc.
Whether /boot is separate partition or just a folder named boot in / (root), it makes no difference. But if the EasyBCD process requires separate /boot partition that's different story. I have no intention to use it like that and don't know the exact procedure. Since you do want to use it, read the information about it and the answer is simple, it either needs separate /boot or not.
Then just set grub2 to install on the /boot partition if there is any (you need to know the exact name, like /dev/sda2), or on your / partition because there is where boot folder will be.

---

### Post by webster922 on 2009-12-05
I finally got it working! Now at startup there is the clean Windows 7 loader with 2 entries, 7 and Ubuntu. Then Windows 7 will chainboot Ubuntu's loader. It has the multiple kernels, both normal and recovery, along with memtest86 and entries for Windows 7. I am glad all of that is not on the Windows 7 bootloader. 
 
Thanks for all the help gabo.cr, louieb, darkod, and misterbk. Your answers were the best response I've gotten on Ubuntu Forums yet.

---

