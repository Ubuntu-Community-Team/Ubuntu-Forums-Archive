---
title: "No option to Install Ubuntu alongside another operating system"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by jimbr on 2010-10-12
I am running Win7 Starter on an LGX130 Netbook - on Sunday I downloaded the latest 10.10 Netbook iso file - today I downloaded the latest USB Installer from Pen - created the USB Mem Drive System - it boots fine (even had Wireless Connection) but was unable to instal alongside my Win7 as the Option Button for " Install Ubuntu alongside another operating system" does not exist - only get the options to; wipe out the existing system and instal Ubuntu or to manually define partitions.

Can anyone help me to get the option to install Ubuntu alongside my Win7 system?

Regards, Jim

---

### Post by C.S.Cameron on 2010-10-12
You could defrag and partition your HDD, then install using manual.

---

### Post by wilee-nilee on 2010-10-12
> **jimbr said:**
> I am running Win7 Starter on an LGX130 Netbook - on Sunday I downloaded the latest 10.10 Netbook iso file - today I downloaded the latest USB Installer from Pen - created the USB Mem Drive System - it boots fine (even had Wireless Connection) but was unable to instal alongside my Win7 as the Option Button for " Install Ubuntu alongside another operating system" does not exist - only get the options to; wipe out the existing system and instal Ubuntu or to manually define partitions.

Can anyone help me to get the option to install Ubuntu alongside my Win7 system?

Regards, Jim

You also want to be sure to have the Windows 7 on board disc manager resize the windows partition, don't use the install partitioner for resizing Windows.

---

### Post by Mark Phelps on 2010-10-12
> **jimbr said:**
> ..Can anyone help me to get the option to install Ubuntu alongside my Win7 system?

Depends on WHY it's not offering you that option in the first place.

One all-too-common problem with pre-installed Win7 machines is that the vendor configures them with 4 primary partitions.  Since that's all you are allowed, the Ubuntu installer has no way to make any more of them.

To see how many you have, you need to start Ubuntu in LiveCD mode (Try it), open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results back here.

If you already have 4 primary partitions, it's going to be a lot of work you your part to install Ubuntu because you can't just shrink one of those you have already.

---

### Post by jimbr on 2010-10-13
Thanks Mark - looks like you are correct - herewith the result requested:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf4ce6456

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3147775     1572864   12  Compaq diagnostics
/dev/sda2         3147776   244320255   120586240    7  HPFS/NTFS
/dev/sda3       244320256   467421183   111550464    7  HPFS/NTFS
/dev/sda4       467421184   488394751    10486784   12  Compaq diagnostics

Disk /dev/sdb: 8032 MB, 8032092160 bytes
5 heads, 32 sectors/track, 98048 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0bf33dd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    15687679     7839808    b  W95 FAT32

NB sda3 is win drive D:/ and is currently unused. I would really appreciate your assistance with making this work. Regards, Jim

---

### Post by jimbr on 2010-10-15
Would be grateful if anyone would point me in the right direction to sort this out so that I can install Ubuntu beside Win7

---

### Post by jimbr on 2010-10-15
:)Problem solved - went in the deep end and deleted my D:/ partition in Windows and booted Ubuntu USB - install went fine - using it now!

---

### Post by Chazz44able on 2010-11-01
[QUOTE=jimbr;9960496]I am running Win7 Starter on an LGX130 Netbook - on Sunday I downloaded the latest 10.10 Netbook iso file - today I downloaded the latest USB Installer from Pen - created the USB Mem Drive System - it boots fine (even had Wireless Connection) but was unable to instal alongside my Win7 as the Option Button for " Install Ubuntu alongside another operating system" does not exist - only get the options to; wipe out the existing system and instal Ubuntu or to manually define partitions.

Can anyone help me to get the option to install Ubuntu alongside my Win7 system?


I've got exactly the same problem but with Windows XP as my other OS trying to install Ubuntu 10.10, it only shows that i have two partitions - the main disk and the "HP Backup" disk (10GB). This obviously means that i cannot simply delete one of the partitions. so what should I do?

---

### Post by Quackers on 2010-11-01
Do you have no free space on the disk? If not you would need to resize your XP partition to make unallocated space for Ubuntu to install in.

---

### Post by Chazz44able on 2010-11-01
I have a 102Gb drive as the main one and i,ve already cleaned it down so that i have 64.7Gb free

---

### Post by Quackers on 2010-11-01
Is that free space within the XP partition or free space on the disk after shrinking XP?

---

### Post by Chazz44able on 2010-11-01
That's free space on the disk full stop, i haven't shrunk the Xp partition

---

### Post by billmarshall on 2010-11-18
> **jimbr said:**
> :)Problem solved - went in the deep end and deleted my D:/ partition in Windows and booted Ubuntu USB - install went fine - using it now!

I have same issue.  Exactly how did you delete the D: partition?

Got it.  I used the Win 7 partition tool to delete D:  Expanded C: to include that space and then installed Ubuntu alongside Win 7 with no problem

---

### Post by SSyar on 2011-01-10
HI, there i am confused at this step 
[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/install_04_medium.jpg[/IMG]
[COLOR=Red]**NOTE: The above image is from ubuntu install page.. not my PC screen shot**[/COLOR]

right now i have 2 partition on my HD, with Win7 on C: and D: is with other files and folder,
i just want to know about the above step that if i select the space,,,,,! for the install of ubuntu will it effect my content on the drive....!

another thing the space which i will select will be a new drive (after shrinking) or will it be on the same drive with Ubuntu files in it..!


Thanx in advance

---

### Post by kansasnoob on 2011-01-10
> **SSyar said:**
> HI, there i am confused at this step 
[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/install_04_medium.jpg[/IMG]
[COLOR=Red]**NOTE: The above image is from ubuntu install page.. not my PC screen shot**[/COLOR]

right now i have 2 partition on my HD, with Win7 on C: and D: is with other files and folder,
i just want to know about the above step that if i select the space,,,,,! for the install of ubuntu will it effect my content on the drive....!

another thing the space which i will select will be a new drive (after shrinking) or will it be on the same drive with Ubuntu files in it..!


Thanx in advance

Please begin by choosing "Try Ubuntu" rather than choosing to install, then from the live desktop please post the output of this command from the terminal:

```
sudo parted -l
```

BTW that's a lower case L.

Just for general info you might find this useful:

[http://ubuntuforums.org/showpost.php?p=10119443&postcount=1](http://ubuntuforums.org/showpost.php?p=10119443&postcount=1)

[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

---

### Post by claven123 on 2011-01-10
I agree, I'm a bit confused about your set up.

Do you have two drives?  C and D?

Or, one drive with two partitions?


If your doing a dual boot the windows partition will be unaffected by the linux partition, anything you do to your linux partition does not affect the windows partition.  Except on the windows partition there are some files for booting that are there, but it does not change windows.

I have linux on several computers in dual boot and on some I never was able to boot and run windows (the reason I switched to ubuntu) and others I boot back and forth all the time.


Boot from live cd and use the try ubuntu method.  Then run gparted and see what you have.  Take a screen shot of it and post that.

Booting live CD will not affect your machine.

Good luck and welcome to ubuntu

Dennis

---

### Post by SSyar on 2011-01-10
I have 1 dirve with 2 partitions C and D, C has Win & D has my data...!
my issue is... i m not sure what will happen when i select the above mention step..!

i hav tried **wubi** but its not working dunno why(i have installed Ubuntu on another machine using wubi it works fine from my CD for desktop)

right now i m booting using my USB for netbook edition ... and then going for the install...!

---

### Post by claven123 on 2011-01-10
Did you run gparted from the live disk.  Ubuntu is going to look for empty hard drive space and install in that space.  If you want it to install in a specific location you will have to choose that location.  I always just let it place it where it wants, but you have control over this. 

You need to determine if you, in fact, have free space or unused disk space.

Run gparted from the live disk and post a screen shot.  Or do the run the terminal command as stated before.

Dennis


BTW: Ubuntu will not overwrite your data or windows, UNLESS you choose to use the entire partition or use the entire disk then your going to have data loss (back up your data).

Also, I was not fond of the netbook edition, preferred the full version if your netbook can support it install that.

---

### Post by SSyar on 2011-01-11
well i m totally new in this ubuntu ... thing..!
didnt hav any idea about Gparted... 



full version?? means Desktop version !
i have the CD, mailed from Ubuntu support of 10.04 desktop version is it OK for a Notebook(Aspire 4741)

---

### Post by kansasnoob on 2011-01-11
@SSyar,

The reason I asked for the output of "sudo parted -l" in post #15 is that Win7 often has "hidden" partitions, specifically a small partition containing part of the boot files, and Windows "drive" designations mean nothing to Linux! Here's an example of Ubuntu device designations:

> Drives are designated as /dev/sda, /dev/sdb, /dev/sdc, etc. the last letter indicates the drive number, eg:
/dev/sda = drive #1
/dev/sdb = drive #2
/dev/sdc = drive #3

Partititions are designated with a number following the drive designations, eg:
/dev/sda1 = drive #1/partition #1
/dev/sda2 = drive #1/partition #2
/dev/sdb1 = drive #2/partition #1

It's up to you whether you install 10.04 or 10.10, which desktop flavor, etc. But the 10.10 installer has one bad bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Be sure and check out the duplicates :(

Clicking on either the "Use entire partition" or "Use entire disc" buttons on that screen you displayed in your original post will very likely erase your existing OS and data!!!!!!!!!!

---

### Post by SSyar on 2011-01-17
well i end up installing 10.04 dekstop version on my notebook :p,,,

every thing worked smoothly...! ! !! but  wubi didnt work on my win7 ...! so booting is from grub which i hate

---

