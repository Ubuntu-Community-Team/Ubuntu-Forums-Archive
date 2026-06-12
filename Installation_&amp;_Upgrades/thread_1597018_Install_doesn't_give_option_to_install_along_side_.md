---
title: "Install doesn't give option to install along side of other OS"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2010-10-14
I am installing ubuntu on a Dell m7750n machine that has the KSOD.  I have done almost everything I can find to fix it.  I was able to remove my data off of it using regedit....  

So, I am sick of MS and found linux.  I installed unbutu netbook on my netbook and it works like a charm.....

So, I went to install this on my desktop dell....  I have read of the many issue with this...

I was not able to boot from the CDlive as is.  I kept getting a black screen with nothing.  I then used the f6 to get into grub and then choose f6 to change the load options to load nomodeset and was able to load ubuntu from the drive, not install.

I would like to install ubuntu, but when I click on install from the 'tester' version it will not give me the option to install along side another OS (windows) that I see in the install ubuntu main website in the see how to do it.

I get two options:
Erase and use entire disk
Specify partitions manually (advanced)


I have searched and searched, but can't seem to get what I need.

Question: Can I install and select my own partitions using:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Or, is there something wrong and I need to get that fixed before I install ubuntu?

Is this a DELL issue or KSOD issue?

---

### Post by oldfred on 2010-10-15
I have always created partitions in advance with gparted, but that takes some planning in advance on what you want. Manual partitioning also gives additional choices for /home or /data or a shared NTFS partition which it looks like you can do directly now in Maverick.

Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

---

### Post by claven123 on 2010-10-15
I just read that Win7 uses/creates 4 partitions, is this the same with vista?  I will run the command and see what is on my machine, just in case.
 
Is running with the nomodeset causing me problems, and should I fix this first before installing ubuntu?
 
When I don't do this the monitor will go directly to sleep/hibernate mode when installing ubuntu or windows for that matter.  I think this is an issue with the output being vga vs dvi?

---

### Post by oldfred on 2010-10-15
Win7 actually uses two partitions on new installs. A 100MB boot/repair hidden partition and a main partition. It was to allow encrypting the main partition but the boot could not be encrypted.  Vista normally installs in one partition. Win7 can be installed in an existing NTFS partition and then it will only use one partition. Vendors then often use one partition as an image of you drive(not really an install CD/DVD) and a utilities partition using all 4 primary partitions on new win7 installs. 

With nomodeset do you get into your system ok, but just low graphics mode. Does it offer to install a proprietary driver? I have Nvidia and have to use nomodeset for liveCD and first boot (or its goes to sleep) but once Nvidia driver is installed it works just fine. I have dvi so that is not the issue, they do not seem to know. My dvi is two channel but the monitor connector is one channel which may be the problem.

---

### Post by claven123 on 2010-10-15
Yes, with nomodeset I can use the liveCD and it all works fine.  It's just when I go to install, it wants me to do a manual partition.  I've never done this and will need to read up on it and learn a bit more before I do.  Otherwise, I believe it will work.  I can go in a adjust the settings that have been suggested in the forums for the nvidia nomodeset issues.  ie change grub2 boot stuff....  I then can install the nvidea drivers etc.....

I just need to get the partition thing in order first.  I would like it if ubuntu would just do this automatically like the directions.... oh well, I guess I will learn more about linux :)



36B00C53-2AE1-7F97-641E-C0B312441395
1.02.28

---

### Post by perspectoff on 2010-10-15
Also try the Alternate CD for installation. 

If you have a graphics incompatibility, the Regular Download CD GUI may not display properly. The Alternate CD has basically a text-based installer (although GUI in appearance).

The Alternate CD has a more transparent installation scheme, as well.

further, the Regular Download LiveCD appears to choose for you whether to use Wubi (installing within Windows) or using Free Space. 

I haven't quite sorted out what it does, yet.

Freedom of choice appears to be disappearing with successive cryptic Ubuntu "simplified" installers. "They" are smarter than you, I guess.

---

### Post by perspectoff on 2010-10-15
> **claven123 said:**
> 
I would like it if ubuntu would just do this automatically like the directions.... oh well, I guess I will learn more about linux :)



No you wouldn't. You should never trust automatic things to go the way you want them to go (seems like the plot of Wall-E).

A little learning goes a long way.

---

### Post by oldfred on 2010-10-15
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)

Make swap larger if you want to Hibernate and have more than 2GB of memory.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

### Post by claven123 on 2010-10-15
further, the Regular Download LiveCD appears to choose for you whether to use Wubi (installing within Windows) or using Free Space.



Interestingly, Windows does not even work on this machine.... It has failed and I can not recover the OS. (black screen of death).

So, can I expect Wubi to be working and or not working.  I didn't use it to install in the first place (knowingly).  I just DL the regular installation files on the main ubuntu page. 

Thanks for the information on what suggested sizes to make the partitions..... very helpful indeed.

Of note, if I choose to erase the entire HD, will this then install ubuntu without me doing anything to the partitions..... manually.


36B00C53-2AE1-7F97-641E-C0B312441395
1.02.28

---

### Post by oldfred on 2010-10-15
Wubi is a file in the NTFS windows partition and uses the windows boot loader. So any issues with windows will prevent wubi from working. For reliability separate partitions are better. Wubi is for a longer test than just using the liveCD and does not require creating new partitions for those who are primarily windows users and may not stay with Ubuntu long term. But most convert to full partitions after using it for awhile.

---

### Post by claven123 on 2010-10-16
I ran this....

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 400.1 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   768292559   384146248+   7  HPFS/NTFS
/dev/sda3       768292560   781416719     6562080    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


I also ran gparted and I get....

The first has an exclamation point in red and the flag is boot, does this mean the first partition is the boot partition and is 366GB is size?  (I know the boot records are in the windows partition)

To change the partitions I will have to shrink the ntfs windows partition to ____ and keep the second one (HP recovery) one 6.26GB.  I only have 2.95MiB of unallocated disk space, I think that is why I can't install ubutu in dual boot.  Ill have to increase the unallocated disk space partition.  

Then I can use the unallocated disk space to make these?  Is this correct..... 

10-20 GB Mountpoint / primary beginning ext4(or ext3)
all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
GB Mountpoint swap logical (or size of RAM memory)


Or, once I shrink the first partition and increase the unallocated space, can I install and let ubuntu install automatically?

BTW, I love linux, as I am typing this on a broken windows machine that is running ubuntu from the LiveCD!!

---

### Post by oldfred on 2010-10-16
Someone posted that the install to free space does not work in 10.10 and you end up manually partitioning anyway.

Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

---

### Post by claven123 on 2010-10-16
My plan was to partition up the large partition occupied by windows....  the 366GB one.  

Or, should I shrink it and make a new partition in the unallocated drive space for unbuntu?

Dennis

---

### Post by oldfred on 2010-10-16
Thats up to you. Just remember you can only have 4 primary partitions. You will want to create one partition as an extended partition and install all your Ubuntu partitions as logical partitions inside the one primary extended.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

If you have Vista or 7 use the windows tools to shrink the windows partition or else you may have problems. It will want to run chkdsk on the resize. Reboot several times to make sure it had adjusted to its new size. You need to leave 20-30% free space in NTFS partitions for them to work well.

---

### Post by claven123 on 2010-10-16
Thanks again for all the help.   However, Windows is dead on this machine.... can i get to those functions from within ubuntu via the liveCD?  That's all I have with this machine...

I will have to read up on the partitions....  a bit more.  I have been reading a bit about this and have read about the 4 partitions...

Thanks.

---

### Post by oldfred on 2010-10-17
You can use gparted but then have to uncheck round to cylinders. Since Ubuntu converted to this it may do it automatically now, not sure.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)
Vista and Partitioning - details
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

---

