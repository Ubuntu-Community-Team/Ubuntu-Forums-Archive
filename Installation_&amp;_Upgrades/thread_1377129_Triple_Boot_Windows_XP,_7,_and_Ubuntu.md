---
title: "Triple Boot Windows XP, 7, and Ubuntu"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by flamefox_9 on 2010-01-09
Hi, i have a question that needs answering. I have an acer aspire 5517 with a dual boot of windows 7 and ubuntu 9.04. Im thinking about making a triple boot by adding windows XP to the mix. Can anyone tell me how to do this and if this is recommended? I am a noob at this sort of thing and ubuntu itself. Thanks in advance!

P.S. I am using GRUB bootloader and i dont want to get rid of it.

---

### Post by garvinrick4 on 2010-01-09
Hello,
 I am going to give you a Link to read about gparted and partitioning. There are certain rules
about Windows installs using primary partitions only. There are 4 available per hard drive so this should help you in your decision on how you should partition your drive. 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by flamefox_9 on 2010-01-10
> **garvinrick4 said:**
> Hello,
 I am going to give you a Link to read about gparted and partitioning. There are certain rules
about Windows installs using primary partitions only. There are 4 available per hard drive so this should help you in your decision on how you should partition your drive. 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Ok, I understand, but my laptop came with system reserved and recovery partitions. These and the two operating systems make 4 primary partitions. What should I do in this case?

---

### Post by garvinrick4 on 2010-01-10
Go to terminal and enter Code:

sudo 'fdisk -l" without qoutes that is small L not and I and post results.

---

### Post by raymondh on 2010-01-10
If your Jaunty and swap are logical partitions inside and EXTENDED partition, then you possible have capability to add 1 more primary partition to house XP.

The rule is 4 primary partitions or 3 primary + 1 extended

If you insist on installing XP in a logical partition .... make sure it is SP2 and, there will be more work to do.  Also note that the bootloader files have to be in primary, active partitions.

[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)
[http://support.microsoft.com/kb/102873](http://support.microsoft.com/kb/102873)

Back-up ... good luck.

Raymond

---

### Post by flamefox_9 on 2010-01-10
> **garvinrick4 said:**
> Go to terminal and enter Code:

sudo 'fdisk -l" without qoutes that is small L not and I and post results.

Here is the result:

```
Device Boot         Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581       36956   284150210    7  HPFS/NTFS
/dev/sda4           36957       38913    15719602+  83  Linux

```

---

### Post by raymondh on 2010-01-10
> **flamefox_9 said:**
> Here is the result:

```
Device Boot         Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581       36956   284150210    7  HPFS/NTFS
/dev/sda4           36957       38913    15719602+  83  Linux

```

I believe one of the primary partitions has to go .... if you insist on installing XP in a 3-boot configuration.

Raymond

---

### Post by Orlando84 on 2010-01-10
Don't forget to back up MBR with your GRUB in case WinXP erases MBR and writes its own loader. To do this you need to run command from console 
```
$dd if=/dev/hda of=MBR-backup bs=512 count=1
```
 And later you can restore MBR using this command 
```
$dd if=MBR-backup of=/dev/hdx bs=512 count=1
```

---

### Post by flamefox_9 on 2010-01-10
> **raymondh said:**
> I believe one of the primary partitions has to go .... if you insist on installing XP in a 3-boot configuration.

Raymond

According to my partition list,
/dev/sda1 is my recovery
/dev/sda2 is my system reserve
/dev/sda3 is Windows 7
/dev/sda4 is Ubuntu

I have the recovery on several disks, so should i get rid of the recovery partition?

---

### Post by flamefox_9 on 2010-01-10
> **Orlando84 said:**
> Don't forget to back up MBR with your GRUB in case WinXP erases MBR and writes its own loader. To do this you need to run command from console 
```
$dd if=/dev/hda of=MBR-backup bs=512 count=1
```
 And later you can restore MBR using this command 
```
$dd if=MBR-backup of=/dev/hdx bs=512 count=1
```
Ok, I'll get that covered. Thanks for the code and reminder.

---

### Post by raymondh on 2010-01-10
> **flamefox_9 said:**
> According to my partition list,
/dev/sda1 is my recovery
/dev/sda2 is my system reserve
/dev/sda3 is Windows 7
/dev/sda4 is Ubuntu

I have the recovery on several disks, so should i get rid of the recovery partition?

You'll have to consult your machine's manual.  In some systems, it's ok to delete the recovery partition once recovery discs have been made.  Some, require a recovery partition still.

What is system reserve?  Is that the 100mb partition win7 installs by default?  On my 3 boot, I have chosen NOT to install that. 


My 3-boot fdisk -l on a 320gb Hd:


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1080654

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7833    62914556+   7  HPFS/NTFS
/dev/sda2   *        7833       31081   186740900   af  Unknown
/dev/sda3           31082       38913    62910540    5  Extended
/dev/sda5           31082       31316     1887606   82  Linux swap / Solaris
/dev/sda6           31317       33230    15374173+  83  Linux
/dev/sda7           33231       38913    45648666   83  Linux

sda1 is win7.  sda2 is OSX.  Sda3 is an extended housing logical partitions for swap, root and /home.  Notice that I do not have the above-mentioned 100mb partition that win7 installs by default.  That, btw, is a bootloader recovery image.

Your call.  Do have a working/tested back-up of your files.  Good luck.

Raymond

---

