---
title: "Installing Windows XP with Ubuntu installed first"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by Scottty on 2012-02-21
Hello

I have Ubuntu 11.10 installed first but would like to be able to boot into Windows XP via a boot loader.

How do I install Windows XP and still have the ability to boot into Ubuntu 11.10. I am worried if I install Windows XP, that I won't be able to boot back into Ubuntu 11.10 via the boot loader.

Please let me know

Scott

---

### Post by darkod on 2012-02-21
You are right, immediately after installing XP you will lose the grub2 bootloader on the MBR, and with that the option to boot ubuntu. But your ubuntu is still there (unless you delete its partitions).

One thing you need to note is that XP will have to be installed onto a primary partition. It can't be installed on logical.

After you install XP and it deletes grub2, have your ubuntu cd at hand and simply restore grub2 to the MBR using this:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Scottty on 2012-02-21
Hello **darkod**

> 
One thing you need to note is that XP will have to be installed onto a primary partition. It can't be installed on logical.

> 
First you need to find out what your drives are called. You can do this by going to a terminal and typing:

sudo fdisk -l

> 
From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
So, still in the terminal, type:

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5


This is what fdisk -l came up with

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   970522623   485260288   83  Linux
/dev/sda2       970524670   976771071     3123201    5  Extended
/dev/sda5       970524672   976771071     3123200   82  Linux swap / Solaris

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           16065   312576704   156280320    f  W95 Ext'd (LBA)
/dev/sdc5           16128   312576704   156280288+   7  HPFS/NTFS/exFAT

Sorry I don't know the device name of my ubuntu drive. Can you let me know which one it is.

Thank-you

Scott

---

### Post by oldfred on 2012-02-21
Your Linux partition is sda1 as it is the  only Linux formated partition.

Which drive were you going to install XP onto? You have 3 drives. 

To install XP, it needs a primary partition as mentioned by Darko but you have to have a boot flag (active partition) on that NTFS partition. Right now you only have a boot flag on sda1. 

Grub does not use boot flag, so you do not need the flag on sda1. Use gparted to managed flags, you can also use Disk Utility or command line. Or in Windows, it is the active partition which you can set when in Windows.

---

### Post by Scottty on 2012-02-21
Hello oldfred

> 
Which drive were you going to install XP onto? You have 3 drives.


I have 1 internal Hard drive of 500GB which I believe has Ubuntu 11.10 on it

I would like to put Windows XP on this drive as well

The other 2 Drives I have are external and I use to backup Data

Can you please let me know where to go to from here.

Thank-you

scott

---

### Post by oldfred on 2012-02-22
Since it is XP, I do not think there is any issue in just shrinking sda1 and creating a new sda3. On the drive the sda2 will be after the sda3 but number order on drive does not matter. 

Some with Windows 7 do have issues with extended partitions in the middle of a drive and installing a new 7 after the extended. Your extended is at the end of the drive.

Shrink sda1 for the size of XP that you want, format it to NTFS and in gparted set boot flag on sda3. 

If dual booting you may want another NTFS partition for shared data. If you want that shrink the Linux partition a little more if you can, and extend the extended partition left into the unallocated space. You then can create a logical NTFS partition for shared data. I use shared data partition for Firebird & Thunderbird profiles and any data I wanted with both systems.


Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Scottty on 2012-02-22
Hello oldfred

Thanks for the help.

I have to admit I'm not to clear on your instructions so I'm going to read the Links you sent me

> 
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/li...s-1/index.html](http://www.ibm.com/developerworks/li...s-1/index.html)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)


If you have anymore suggestions please let me know

I will probably be asking you more questions in the near future.

Cheers

Scott

---

