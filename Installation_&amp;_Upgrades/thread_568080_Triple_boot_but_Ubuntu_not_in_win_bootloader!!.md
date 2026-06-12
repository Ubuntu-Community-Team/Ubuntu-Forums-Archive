---
title: "Triple boot but Ubuntu not in win bootloader!!"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by Ncdude on 2007-10-05
Hey everyone,

I have Winxp and Vista on a Sata drive along with Ubuntu but when Ubuntu installed it did not get on the bootloader. All I have as choices are WinXP and vista. Is there a simple way to add Ubuntu to the bootloader that Windows uses? 

Thanks,

Scott..

---

### Post by Xavier Oddmon on 2007-10-05
I'm no expert, but I believe that you're supposed to install Ubuntu last. It won't show up on the windows boot loader, you should use Grub. What order did you install them in?

---

### Post by Ncdude on 2007-10-05
Ubuntu was installed last.

---

### Post by ak825989 on 2007-10-05
Use the 'Bootpart' utility to add an entry to 'boot.ini' and a ubuntu boot sector file into your Win boot drive - downloadable from [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

However, I think this assumes you have GRUB installed on the boot partition for your ubuntu installation.

Give it a go, and let us know what happens!

---

### Post by confused57 on 2007-10-05
You might be able to use EasyBCD:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Grub has to be installed to Ubuntu's root partition for this to work, but it can easily be done with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Ncdude on 2007-10-05
OK I have Bootpart running but I am not sure about the command line

BOOTPART <part_number> [LBA] <filename> [<name_of_system>]

part number I think is 16

LBA ??

File name ??

Thanks,

Scott..

---

### Post by ak825989 on 2007-10-05
Hiya!

Can't tell you what the part number is, depends on your partitioning scheme, but it'll be a type 83 for an ext3 partition

Specify LBA - (logical block addressing) more efficient if your system supports it, which it will unless you've had it years.

Filename - the name of the file that will be created in your Win boot drive - you can call it anything, but ubuntu.bt might be a good choice - gives you a clue as to what it is!

Name of System - what will appear in 'boot.ini' - again, can call it anything, but 'Ubuntu' might be a good choice! 

So, command might be:

bootpart 16 ubuntu.bt Ubuntu

bootpart /? will give you a help screen (but I guess you already know that!)

---

### Post by Ncdude on 2007-10-05
Great thanks I am going to try it out.

---

### Post by Ncdude on 2007-10-05
No luck, it hung with an error about can't load harddisk

---

### Post by ak825989 on 2007-10-05
Did you try it with LBA? (My suggested command omitted this - unhelpfully!):

bootpart 16 LBA ubuntu.bt Ubuntu

---

### Post by Ncdude on 2007-10-05
Yes I did and still had the same results, damn it!!

---

### Post by Ncdude on 2007-10-05
I tried EasyBCD and put in all the correct info for Linux and still come up with the same error.

---

### Post by ak825989 on 2007-10-05
Could you output the result of running bootpart to a text file, then cut and paste the text here (if your disk configuration is not a state secret)? Eg

bootpart > c:\disks.txt

---

### Post by Ncdude on 2007-10-05
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Scott>cd..

C:\Documents and Settings>cd..

C:\>bootpart
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : [http://www.winimage.com](http://www.winimage.com) and [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : 29d4940c
 0 : C:* type=f  (Win95 XInt 13 extended), size= 195350400 KB, Lba Pos=16065
 1 : C:  type=7   (HPFS/NTFS), size= 48837568 KB, Lba Pos=16128
 2 : C:  type=5   (Extended), size= 48837600 KB, Lba Pos=97691265
 3 : C:  type=7    (HPFS/NTFS), size= 48837568 KB, Lba Pos=97691328
 4 : C:  type=5    (Extended), size= 48837600 KB, Lba Pos=195366465
 5 : C:  type=7     (HPFS/NTFS), size= 48837568 KB, Lba Pos=195366528
 6 : C:  type=5     (Extended), size= 48837600 KB, Lba Pos=293041665
 7 : C:  type=7      (HPFS/NTFS), size= 48837568 KB, Lba Pos=293041728
Physical number of disk 1 : 25d80ed4
 8 : D:* type=7  (HPFS/NTFS), size= 49295421 KB, Lba Pos=63
 9 : D:  type=f  (Win95 XInt 13 extended), size= 439088580 KB, Lba Pos=98590905
10 : D:  type=7   (HPFS/NTFS), size= 47889733 KB, Lba Pos=98590968
11 : D:  type=5   (Extended), size= 47889765 KB, Lba Pos=194370435
12 : D:  type=7    (HPFS/NTFS), size= 47889733 KB, Lba Pos=194370498
13 : D:  type=5    (Extended), size= 313082752 KB, Lba Pos=290149965
14 : D:  type=7     (HPFS/NTFS), size= 313082721 KB, Lba Pos=290150028
15 : D:  type=5     (Extended), size= 14651280 KB, Lba Pos=916315470
16 : D:  type=83      (Linux native), size= 14651248 KB, Lba Pos=916315533
17 : D:  type=5      (Extended), size= 15366172 KB, Lba Pos=946035720
18 : D:  type=7       (HPFS/NTFS), size= 15366141 KB, Lba Pos=946035783

C:\>bootpart c:\disks.txt
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : [http://www.winimage.com](http://www.winimage.com) and [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : 29d4940c
 0 : C:* type=f  (Win95 XInt 13 extended), size= 195350400 KB, Lba Pos=16065
 1 : C:  type=7   (HPFS/NTFS), size= 48837568 KB, Lba Pos=16128
 2 : C:  type=5   (Extended), size= 48837600 KB, Lba Pos=97691265
 3 : C:  type=7    (HPFS/NTFS), size= 48837568 KB, Lba Pos=97691328
 4 : C:  type=5    (Extended), size= 48837600 KB, Lba Pos=195366465
 5 : C:  type=7     (HPFS/NTFS), size= 48837568 KB, Lba Pos=195366528
 6 : C:  type=5     (Extended), size= 48837600 KB, Lba Pos=293041665
 7 : C:  type=7      (HPFS/NTFS), size= 48837568 KB, Lba Pos=293041728
Physical number of disk 1 : 25d80ed4
 8 : D:* type=7  (HPFS/NTFS), size= 49295421 KB, Lba Pos=63
 9 : D:  type=f  (Win95 XInt 13 extended), size= 439088580 KB, Lba Pos=98590905
10 : D:  type=7   (HPFS/NTFS), size= 47889733 KB, Lba Pos=98590968
11 : D:  type=5   (Extended), size= 47889765 KB, Lba Pos=194370435
12 : D:  type=7    (HPFS/NTFS), size= 47889733 KB, Lba Pos=194370498
13 : D:  type=5    (Extended), size= 313082752 KB, Lba Pos=290149965
14 : D:  type=7     (HPFS/NTFS), size= 313082721 KB, Lba Pos=290150028
15 : D:  type=5     (Extended), size= 14651280 KB, Lba Pos=916315470
16 : D:  type=83      (Linux native), size= 14651248 KB, Lba Pos=916315533
17 : D:  type=5      (Extended), size= 15366172 KB, Lba Pos=946035720
18 : D:  type=7       (HPFS/NTFS), size= 15366141 KB, Lba Pos=946035783

C:\>

---

### Post by ak825989 on 2007-10-05
Can I just check - when do you get this 'cannot load from harddisk' error?

When you run bootpart, or when you try to boot from boot.ini, using the bootpart created entry?

---

### Post by Ncdude on 2007-10-05
When I select Ubuntu from the windows boot menu. But WindowsXP and Vista work fine.

---

### Post by ak825989 on 2007-10-05
Congratulations! You're now stuck where I am!

I think the problem is about getting GRUB installed on the relevant linux partition, and I am actively working on this. Go to this thread for more info - 

[http://ubuntuforums.org/showthread.php?t=568170](http://ubuntuforums.org/showthread.php?t=568170)

and watch that space!

---

