---
title: "ATA HD as SATA in GRUB"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by sysmacons on 2008-11-08
My DELL PRECISION 650 runs on both WINDOWS 2000 and SUSE 10 with LILO. The system has three harddrives, the boot one on built-in IDE controller, channel 1, and the other two on an add-on PROMISE ULTRA100 IDE controller, each on its own channel. All disks and controllers are IDE. No SATA disk or controllers are on board.

I decided to change from SUSE 10 to KUBUNTU 8.041. I grabbed the KUBUNTU live DVD and proceeded to install. All went ok but when re-booting I just got a bliking L on the screen. After a short investigation I found out that GRUB installed itself on hd(0), which however was not my boot device on the built in controller, but rather the first HD on the PROMISE add-on card. The boot device was identified as "sda" or hd(2). I fired the live DVD and re-configured GRUB to sda (actually, hd(2) in GRUB language). This time at boot I got my screen filled with thousands of "GRUB", and useless to say it did not boot. 

I tried to re-install from live DVD and from alternate CDROM setting GRUB in /dev/sda and then hd(2), both KUBUNTU and UBUNTU. But the result was always the same. I also tried to re-configure by hand the device.map and menu.lst, with no luck.

Since my system was basically un-bootable and I needed to complete some work I had to go back to my old SUSE 10 (which is still on).

Now the questions. 
1) Why does KUBUNTU/UBUNTU installer read my first HD on the built-in IDE controller as a SATA device? What can I do to avoid this at installation time?

2) If this behaviour is un-avoidable, how can I have GRUB configured correctly on my first HD on the built-in IDE controller at installation time?

Thanks in advance for your help.

---

### Post by louieb on 2008-11-08
1. The Ubuntu sata controller handles both ide and sata drives. Been that way since v6.10.  Just have to live with it.

2. ide + sata drives on same computer sometimes leads to grub-install confusion. Don't have a mixed drive computer so haven't had to fix grub in that case. But heres a decent thread on the subject.    [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by sysmacons on 2008-11-08
Thanks louieb.

Point is that I have no SATA disks. It is UBUNTU that thinks that my ATA drive on the first channel of the built-in controller is a SATA. But it correctly gets the other two drives on the add-on PROMISE ULTRA100 controller as ATA.

I will go and look into the link you sent me.

---

### Post by sysmacons on 2008-11-09
louieb I followed the guidelines in the links you gave me. Result, GRUB now starts up showing both KUBUNTU and WINDOWS2000. But if I select KUBUNTU I get ERRROR 22 message, and if I select WINDOWS2000 I receive similar message (cannot find NTLDR, which of course is there). I checked and everything matches the actual location of files on the drives and configuration. I also tried to use LILO, but it reports an error due to the way the drives are addressed in fstab.

So at the end I went back to my old SUSE10 installation which recognizes IDE drives as IDE drives, with LILO as a boot loader.

What a pity, KUBUNTU works so well on my laptop.

If someone have more suggestions, like for instance how to make LILO working as the default boot loader at installation time, I am here to listen.

---

### Post by louieb on 2008-11-09
Can you get Suse to boot kubuntu? still sounds like GRUB is getting the boot order confused or doesn't have the drives mapped right.   

If you can get kubuntu up and running there  a couple of commands to try 
in a terminal window start grub with privileges
```
sudo grub
```now to find the kubuntu partition 
```
find /boot/grub/stage1
```use whatever that returns in your kubuntus root statment in menu.lst  that should get rid of the error 22.

now to figure out where windows is.
 ```
geometry (hd
```  and press the [COLOR=Red]**tab key **[/COLOR]
that will return someting like this **Possible disks are:  hd0 hd1** 

and then check each disk 
 ```
geometry (hd0,
```  and pres the [COLOR=Red]**tab key** 
[/COLOR] that will return some like
> 
 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 6,  Filesystem type is ext2fs, partition type 0x83
some where in there your going to find the partition with a filesystem of NTFS. I don't have windows on this PC so don't have an a example of what to look for. 

Anyway  somewhere in there will be the partition you need for your windows 2000 root statment.  My guess is that you have more that 1 partition with an NTFS file system and just have to figure out which one to use.

Not any help with LILO tried it once and decided to stick with learning GRUB.

---

### Post by caljohnsmith on 2008-11-09
Sysmacons, if you can get as far as the Grub menu on start up, and you get a Grub error when selecting an OS, then that means you have a problem with Grub's menu.lst; fortunately, in most cases menu.lst problems are usually easy to fix. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Kubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Please post the output of that, and it will most likely give us enough info to help you get Grub working again. :)

---

### Post by sysmacons on 2008-11-19
Thanks caljohnsmith. I had to re-install SUSE10 to use my PC so I cannot post the contents of menu.lst. I can however confirm that last time I looked at it it was perfectly matching device.map which in turn matched the output of fdisk -lu.

As I said in my original post I have neither SCSI nor SATA dirves on my machine. My three disks are connected as follows:

1 ATA disk connected as master to the first channel of the built-in IDE controller (that is my WinXP C:\ disk), seen by SUSE10 as hda and by UBUNTU/KUBUNTU as sda;
1 ATA disk connected as master to the first channel of a PROMISE ULTRA100 add-on controller card (with only NTFS aprtitions) seen by SUSE10 as hde and by by UBUNTU/KUBUNTU as hda;
1 ATA disk connected as master to the second channel of a PROMISE ULTRA100 add-on controller card  seen by SUSE10 as hdg and by by UBUNTU/KUBUNTU as hdb (NTFS partitions plus /boot on hdg6, swap on hdg7 and / on hdg8.

During install I selected to install the boot loader on the MBR of /dev/sda (i.e. on the mrb of the ATA disk connected as master to the first channel of the built-in IDE controller). When I tried to boot I got  my screen filled with thousands of "GRUB", and useless to say it could not boot at all. Basically I did not even get to the OS selection menu. I tried other solutions that I found while googling around for a solution, but to no avail.

As soon as I have some time I will try again, this time installing the boot loader to a floppy. I also would like to change from GRUB to LILO, but I could not yet find how to do it (no choice option to do so during install).

Anyhow I will post the outcome of next steps ASAP.

One last thing, I tried to install SUSE11 and this time all three disks were identified as SDX. Funny, isn't it? Install eventually failed because of corrupted media.

Thanks for your time and advise.

Regards.

---

