---
title: "cannot install ubuntu alongside windows 7 - prompt restart to continue"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by tasos2 on 2014-03-20
Hi,

i am trying to install ubuntu alongside win7 and the problem is that when i select to install the ubuntu side by side the win7, the bottom right button turns to "Restart to Continue" and when i press it, the computer restarts saying to remove any media and close the tray, and then it logs in at windows7.
I tried to shrink my win7 partition and i created an 100gb free space to install ubuntu, but still the problem remains the same.
Do you have any ideas how can i bypass the restart?
it's not the first time that i install ubuntu with windows 7 in dual boot and i don't remember this "restart to continue" button..

Thank you

---

### Post by ajgreeny on 2014-03-20
How did you shrink the windows partition?  That behaviour is certainly not normal.

When you get to the partitioning stage of the install use "Something Else" and point to the free space (or is it a partition?) and see if you can then make the partitions you want and proceed further.

---

### Post by tasos2 on 2014-03-20
I used the disk management of the windos to shrink the partition.
I tried with "Something Else" but when i select the free space it sth about root which i don't remember clearly, and i cannot continue.
Is it wrong that i shrunk my partirion?

---

### Post by ajgreeny on 2014-03-20
No probably not wrong, but without knowing your current setup and the exact error message it is difficult to know what more to say.

Can you also check that the install medium is a good copy, by checking the iso file you downloaded against the hashes at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by Mark Phelps on 2014-03-20
> when i select to install the ubuntu side by side the win7

This could mean a couple of very different situations ...

Are you booting directly from the Ubuntu install media when you are doing this?

Or, are you trying to do the installation from INSIDE MS Windows?

---

### Post by tasos2 on 2014-03-21
I am booting from the ubuntu cd (which means i set the bios to read from the cd-rom first) and then i follow the procedure.

@[**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747") It's not an error message. I just click on the first option at the Installation type and the bottom right button says "Restart to continue" instead of "Continue".

With the "Something else" option, the problem is that i cannot create another primary partition, so i cannot use the free space that i created to install ubuntu there.. Any help?

---

### Post by Mark Phelps on 2014-03-21
We need to see the partitions on your drive.  Boot using the Ubuntu media, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  Post that information back here.

---

### Post by tasos2 on 2014-03-22
Hi,

here are the results:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7be45bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      616447      307200   de  Dell Utility
/dev/sda2          616448     6907903     3145728    c  W95 FAT32 (LBA)
/dev/sda3   *     6907904     7112703      102400    7  HPFS/NTFS/exFAT
/dev/sda4         7112704  1953523711   973205504    7  HPFS/NTFS/exFAT

---

### Post by Mark Phelps on 2014-03-22
You already have the maximum of four partitions on the drive.  The installer detects this and won't continue.

If you really want to dual-boot this PC, a LOT of work is involved. You should read through the details below before continuing:

Since you already have four partitions, that is the maximum allowed. You will have to remove a partition before continuing.  To do this, you will 
have to decide which partition to remove. Preinstalled Win7 PCs typically come with a small boot partition, a large OS partition, a Recovery partition, and (in the case of HP) a Tools partition.  

If you have this last one, that's the logical one to remove. So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS 
partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition. 
Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition 
to that drive.  Then, use the MR option to create and burn a Linux Boot CD. Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot 
install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by m340 on 2014-05-27
Wow, thanks for that very complete explanation. I have the same problem exactly as tasos2 and I have exactly the four partition problem you describe. I will be keeping a copy of your answer for the future. For now, I think I will just install 12.04 through WUBI. Thanks again.

---

