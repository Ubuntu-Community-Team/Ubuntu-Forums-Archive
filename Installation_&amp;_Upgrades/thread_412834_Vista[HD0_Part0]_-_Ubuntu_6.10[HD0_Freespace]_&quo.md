---
title: "Vista[HD0 Part0] - Ubuntu 6.10[HD0 Freespace] &quot;Missing Operating System&quot; upon reboot"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by Darkiran on 2007-04-18
So when I installed Vista I installed it on my 100 GB Maxtor hard drive, fully partitioned as NTFS.  I decided to try dual booting the install with Ubuntu and have encountered a problem.

1st I used the disk management within Vista to resize my partition to free up around 30gb's for Ubuntu and then booted off of the Ubuntu 6.10 install CD.   Once loaded up I clicked on the Install icon on the desktop and filled out the appropriate information.  Got to the partition section and selected the "Use free space" option which successfully set up the partitions necessary for Ubuntu and installed it.

The problem is that once Ubuntu was installed and I rebooted my PC it appears to Grub isn't working cause I get a "No Operating System Found" error upon boot.

I deleted the new partitions using the ubuntu CD and tried again and got the same results.

Any help here would be great?

---

### Post by ajgreeny on 2007-04-18
I think you need to use the manual partitoner when you get to that point in the install procedure, not allow the installer to use free space as that will just resize the windows partition again, if I remember correctly.

When you get the partition table showing, it will then show your windows partition and the separate free one, whether or not it is already formatted, in fact you may just as well leave the formatting to the installer.  Chose that free partition and then go ahead with the installation on that 30GB and hopefully all will be well.

It is also worth checking again with the live CD what your partitions already are. Open a terminal and type:-
sudo fdisk -l

This will list your current partitions and give a clue as to where you are at present.

---

### Post by Darkiran on 2007-04-18
I'll try it out once I get home tonight.

---

### Post by Darkiran on 2007-04-18
Here are the results from the "sudo fdisk -l" before any additional TS was done.

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8613    69179392    7  HPFS/NTFS
/dev/sda2   *        8614       12038    27511312+  83  Linux
/dev/sda3           12039       12188     1204875    5  Extended
/dev/sda5           12039       12188     1204843+  82  Linux swap / Solaris

Disk /dev/hda: 30.0 GB, 30020272128 bytes
240 heads, 63 sectors/track, 3877 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3877    29310088+   c  W95 FAT32 (LBA)

---

### Post by Darkiran on 2007-04-18
The HDD I'm installing on is a SATA drive instead of IDE.  Is that going to make any difference?

---

### Post by Darkiran on 2007-04-19
So I ended up having to reinstall Vista cause the partitions got totally freaked out.

Now that I have a fresh install of vista, how do I go about installing ubuntu.  I've seen some guides on setting up dual boots but even those don't seem to explain everything.

---

### Post by ajgreeny on 2007-04-19
Just in case this is one of the guides you missed, have a look at this site:-
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I think it is probably about the most simple way to explain how to get a dual booting system running safely and without problem.  I know this is about windows XP, but the procedure is exactly the same with vista, or so I'm lead to believe.  Note that it is easier to let the installation reduce your windows partition size, not do it beforehand.

Even though you have only just installed vista, I recommend you defrag your windows, maybe twice, before you do the ubuntu install.  This of course assumes vista still needs defraging like previous windows versions did.  I have not yet seen vista, and have no intention of getting it in future.

---

### Post by Darkiran on 2007-04-19
One of the issues I think I'm having is that at the summary screen before the installation starts, it actually asks where the Grub installer is going.  by default it offers me    (hd0)   should I change this to /dev/sda2?  /dev/sda1

---

### Post by Darkiran on 2007-04-19
Language: English
 Keyboard layout: U.S. English
 Name: Nicholas T. Sunde
 Login name: darkiran
 Location: America/Los_Angeles
 GRUB will be installed to (hd0)


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The following partitions are going to be formatted:
 partition #2 of SCSI1 (0,0,0) (sda) as ext3
 partition #5 of SCSI1 (0,0,0) (sda) as swap

---

### Post by Darkiran on 2007-04-20
So I did do the install (I set up the partitions myself this time, left the initial windows partition as the boot partition and let Grub install on "(hd0)".)

Upon reboot it took me straight into Vista, no recognition of Ubuntu at all.  So I installed EasyBCD and set up the Grub multi-but on Hard drive 1, partition 2 which upon reboot and selection of the "Ubuntu" OS does take me to grub with it's many options, however none of them actually boot into anything.  It just errors out.

Atleast Vista didn't get hosed this time.

---

