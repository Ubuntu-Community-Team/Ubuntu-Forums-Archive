---
title: "Wrong unallocated space"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by foxweb on 2011-09-23
I want to rebuild the partitions on HDD. gparted does not see the partition table, but shows the wrong unallocated space. At the same time, Disk Utility shows all the partitions and false unallocated space (it is unrealistic huge, millions of terabytes)

how to fix this partition, without affecting the working partitions? fdisk is not helping.

see screenshots.

Thanks.)

---

### Post by coffeecat on 2011-09-23
Gparted gives you the unallocated message you're seeing when there are certain partition table irregularities. I don't know about Disk Utility, but that might be due to a partition table inconsistency as well. Post the terminal output of:

```
sudo fdisk -lu
```

You can copy and paste the output into your post by highlighting the output with the mouse, and right-click -> copy. Please enclose the output between [noparse]```
 and 
```[/noparse] tags to retain correct formatting of the output.

---

### Post by foxweb on 2011-09-23
sudo fdisk -lu gives some like this:

```


ubuntu@ubuntu:~$ sudo fdisk -lu

&#1044;&#1080;&#1089;&#1082; /dev/sda: 500.1 &#1043;&#1041;, 500107862016 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 60801 cylinders, &#1074;&#1089;&#1077;&#1075;&#1086; 976773168 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
Units = &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1099; of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25f025ef

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sda1   *          63   409593239   204796588+   7  HPFS/NTFS
/dev/sda2       409593301   976768064   283587382    f  W95 &#1088;&#1072;&#1089;&#1096;&#1080;&#1088;. (LBA)
/dev/sda5       409593364   937048000   263727318+   7  HPFS/NTFS
/dev/sda6       937048064   975026175    18989056   83  Linux
/dev/sda7       975028224   976773119      872448   82  Linux &#1089;&#1074;&#1086;&#1087; / Solaris

&#1044;&#1080;&#1089;&#1082; /dev/sdb: 4009 &#1052;&#1041;, 4009754624 &#1073;&#1072;&#1081;&#1090;
124 heads, 62 sectors/track, 1018 cylinders, &#1074;&#1089;&#1077;&#1075;&#1086; 7831552 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
Units = &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1099; of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ee9dd

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sdb1   *          62     7826383     3913161    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 


```

---

### Post by coffeecat on 2011-09-23
Yes, there's a partition table irregularity.

> **foxweb said:**
> sudo fdisk -lu gives some like this:

```


ubuntu@ubuntu:~$ sudo fdisk -lu

&#1044;&#1080;&#1089;&#1082; /dev/sda: 500.1 &#1043;&#1041;, 500107862016 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 60801 cylinders, &#1074;&#1089;&#1077;&#1075;&#1086; 976773168 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
Units = &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1099; of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25f025ef

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sda1   *          63   409593239   204796588+   7  HPFS/NTFS
/dev/sda2       409593301   [COLOR="Red"]976768064[/COLOR]   283587382    f  W95 &#1088;&#1072;&#1089;&#1096;&#1080;&#1088;. (LBA)
/dev/sda5       409593364   937048000   263727318+   7  HPFS/NTFS
/dev/sda6       937048064   975026175    18989056   83  Linux
/dev/sda7       975028224   [COLOR="Red"]976773119[/COLOR]      872448   82  Linux &#1089;&#1074;&#1086;&#1087; / Solaris

&#1044;&#1080;&#1089;&#1082; /dev/sdb: 4009 &#1052;&#1041;, 4009754624 &#1073;&#1072;&#1081;&#1090;
124 heads, 62 sectors/track, 1018 cylinders, &#1074;&#1089;&#1077;&#1075;&#1086; 7831552 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
Units = &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1099; of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ee9dd

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sdb1   *          62     7826383     3913161    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 


```

Your sda7 logical partition has an end sector outside of the extended sda2 partition. I've not seen this particular inconsistency before but this is probably what is causing the problem.

I'll give you two links, but I suggest you read them and not use them just yet. The first is for fixparts:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Which will fix the commoner problem where the extended partition's end sector is beyond the physical end of the hard drive (and also some other issues), but I'm not 100% sure it will deal with what you are seeing.

Also an older link by the same author for using sfdisk to edit the partition table for the extended partition end-sector problem:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

The reason I suggest you not to  use them just yet is that I am not 100% sure whether there is a hidden trap in the situation you have. I am going to pm the author of those links, who is a member of the forum, and ask him to comment.

---

### Post by foxweb on 2011-09-23
Thanks!

So, I've just installed and typed ```
gdisk /dev/sda
```

```

Command (? for help): p
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2D0CE4D9-7C59-4F61-8D66-A01CFCD49E87
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 1-sector boundaries
Total free space is 2279 sectors (1.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63       409593239   195.3 GiB   0700  Linux/Windows data
   5       409593364       937048000   251.5 GiB   0700  Linux/Windows data
   6       937048064       975026175   18.1 GiB    0700  Linux/Windows data
   7       975028224       976773119   852.0 MiB   8200  Linux swap

Command (? for help): d 7
Partition number (1-7): 7

Command (? for help): p
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2D0CE4D9-7C59-4F61-8D66-A01CFCD49E87
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 1-sector boundaries
Total free space is 1747175 sectors (853.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63       409593239   195.3 GiB   0700  Linux/Windows data
   5       409593364       937048000   251.5 GiB   0700  Linux/Windows data
   6       937048064       975026175   18.1 GiB    0700  Linux/Windows data

Command (? for help): ?
b	back up GPT data to a file
c	change a partition's name
d	delete a partition
i	show detailed information on a partition
l	list known partition types
n	add a new partition
o	create a new empty GUID partition table (GPT)
p	print the partition table
q	quit without saving changes
r	recovery and transformation options (experts only)
s	sort partitions
t	change a partition's type code
v	verify disk
w	write table to disk and exit
x	extra functionality (experts only)
?	print this menu

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed, possibly destroying your data? (Y/N): y
OK; writing new GUID partition table (GPT).
The operation has completed successfully.

```

---

### Post by coffeecat on 2011-09-23
I see. You've converted your partition table to a GUID partition table. I think I'll let the person I've pm'd to comment on that.

---

### Post by srs5694 on 2011-09-23
Foxweb,

I'm afraid you've just made the matter worse. The FixParts program that coffeecat recommended would probably have fixed the problem entirely and easily; however, you ran gdisk, not FixParts. The result is that you've deleted your swap partition and converted the disk from the Master Boot Record (MBR) format to the GUID Partition Table (GPT) format. Unfortunately, Windows won't boot from a GPT disk, and the Linux boot loaders for MBR and GPT are different, so Linux no longer boots (unless you re-install GRUB 2).

To fix the problem you'll have to do a reverse conversion, re-install GRUB 2, and re-create a swap partition. There are many variants on this procedure that will work, but one that should do the trick is:


[list=1]
[*]Download the [PartedMagic](http://partedmagic.com) and [Super GRUB 2 Disk](http://www.supergrubdisk.org) images and burn CDs from them. (Note that you want the Super GRUB *2* Disk, not the Super GRUB (no *2*) Disk, unless you've switched from Ubuntu's default of GRUB 2 to GRUB Legacy.)
[*]Boot using Parted Magic.
[*]Launch gdisk on the disk, as in "gdisk /dev/sda".
[*]Type "r" to enter the recovery & transformation menu.
[*]Type "g" to do a GPT-to-MBR conversion.
[*]Type "p" to view the partition table. Ensure that every partition is included in the conversion (none should be listed as "omitted" under the "status" column. Also, ensure that your first (NTFS) partition is listed as "primary" under the "status" column. Your remaining partitions may be either primary or logical. They were originally logical partitions, and setting them as such (via the "L" command, if necessary) may be desirable. If you don't understand something or if anything is listed as "omitted" or missing entirely from the list, type "q" to quit and post back for more help.
[*]Type "w" to save your changes.
[*]Respond "Y" to the verification query. The program should finalize the conversion and terminate.
[*]Launch GParted on the disk.
[*]If one doesn't exist, create an extended partition. If it exists, expand it to fill all the remaining space on the disk.
[*]Create a new swap partition in the free space on the disk.
[*]Reboot into Super GRUB 2 Disk. This should give you a series of menus that will enable you to locate and boot from your normal GRUB 2 installation. You may need to try a few options before you find your system. Find it and boot your computer. It should boot normally.
[*]In a shell, type "sudo grub-install /dev/sda" to re-install GRUB.
[*]Type "sudo blkid | grep swap" to obtain the UUID of your new swap space. This UUID is a long number, such as 90dfc155-fd37-4e73-a112-472ce434096c.
[*]Edit /etc/fstab with your favorite editor. (You'll need to use sudo, gksudo, or some other means to do this as root.)
[*]Locate your existing entry for swap space and replace the UUID with the one you obtained with blkid.
[*]Save the change to /etc/fstab and exit from the editor.
[*]Remove the Super GRUB 2 Disk from the optical drive.
[*]Reboot. Your system should boot normally.
[*]Once you've rebooted, open a Terminal and type "free -m". The final line should begin with "Swap" and contain a non-0 value under the "total" column. This indicates how much swap space is available. If this line specifies "0" under the "total" column, then something is wrong with your re-creation of the swap space -- perhaps you cut-and-pasted the wrong UUID into the /etc/fstab file.
[/list]

---

### Post by foxweb on 2011-10-19
srs5694, thank you for the great manual!

---

