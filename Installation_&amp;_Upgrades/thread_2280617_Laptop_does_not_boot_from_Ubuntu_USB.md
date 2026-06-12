---
title: "Laptop does not boot from Ubuntu USB"
date: 2015-06-01
forum: Installation &amp; Upgrades
---

### Post by eMshsWE on 2015-06-01
Hello,

I have a HP Pavilion dm4 1050 c Laptop dual booted with Windows 7 and Fedora 14. Windows 7 was continously crashing, so  I thought of trying to reinstall Windows 7 through USB.  However, it didnt allow me to install. So I deleted  both my primary partiitons of Windows and Fedora and then tried to install Windows 7 again. It failed.

So I thought, why not try Ubuntu 14.04? so i took one of my USB Pen drives, went to another  Dell laptop, Downloaded the ISO and burnt it to my USB stick. Now when I try to boot from  USB for Ubuntu 14.04, it is not even recognizing the USB stick. Only two options are coming for installation - from Notebook hard Drive and CD/ DVD.

I dont have any of the Ubuntu or Windows CDs, and I deleted my primary partitions, so my laptop has no OS. I m completely stuck here.

I am not able to do anything with my laptop. Why is it not recognizing USB drive of Ubuntu 14.04 ? When I went to the BIOS, it shows options USB Diskettte on Key/ USB hard drive, but does not recognize the USB drive on startup.

When I tried booting from USB on the Dell Laptop it works fine. I have a laptop without an OS, please could someone help me out?

---

### Post by grahammechanical on 2015-06-01
The BIOS might be seeing the USB stick as an external USB hard drive. You may need to find a BIOS setting where you can select which hard drive to boot from. This is what I have to do on my BIOS machine when I want to load a Ubuntu USB memory stick. On my machine it is not enough to set the boot priority I have to select the USB memory stick as a hard drive.

Regards.

---

### Post by eMshsWE on 2015-06-01
How to set the BIOS setting ? In BIOS boot option it shows USB Diskette on Key Press / USB Hard Drive but when I boot it it doesnt detect the USB.

---

### Post by RobGoss on 2015-06-01
How old is that laptop you're using? Also try using a different USB port there maybe something wrong with the current one your using. 

Second: is there any way for you to download a copy of Ubuntu ISO on a DVD? assuming you have a DVD drive in that laptop.

---

### Post by Mike_Walsh on 2015-06-01
When you say you 'burnt' the .iso file to USB, what exactly do you mean? How exactly did you do it?

I tried running a DVD of Fedora 22 on my desktop Compaq the other day. The DVD completely mucked up the settings on all THREE of my Puppy Linux installs.....and I'm still trying to figure out how it did so!

I've been trying to get a USB install of Damn Small Linux to boot on my desktop for the last fortnight, but no matter how I configure the BIOS, the machine simply refuses to 'see' it. Graham's right; you sometimes need to change multiple settings in the BIOS to get things to work... (if you're lucky!) [-o<


Regards,

Mike. ;)

---

### Post by gordintoronto on 2015-06-02
Have a look at Plop boot manager.

Plop Boot Manager will fit on a floppy (or CDR), and can chain to a bootable USB device. [http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

---

### Post by Neill_R on 2016-02-10
Hello i also have problem 

I have a HP G61 laptop and I am trying to boot from a USB Stick. Now the  bios allows booting from the data stick. and the USB does boot okay in that mode.  But i want to test plop CD so I boot from that CD and choose USB. The Grub menu appears but then nothing not even memory test. What am I missing?

---

### Post by sudodus on 2016-02-10
I see no reason to try Plop in a computer that can boot directly from a USB stick.

Plop was made for very old computers. Maybe your computer lacks some feature that is used when booting via Plop. I have used it in an old Compaq Presario 5640 desktop computer with a Pentium II processor. That computer needed it to boot from USB. But Plop does not work for me in some newer computers.

---

### Post by Neill_R on 2016-02-10
One uses the equipment one has and I do want to test booting my USB data stick via plop to see it working which at the moment it doesn't and I do not know how to investigate why. I am writing this from the OS on the same USB data stick booted via BIOS Plop CD not inserted. 

All I see via Plop is the Grub 2 menu on the USB data stick.

auser@Integral16gb:~$ uname -a
Linux Integral16gb 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:23:34 UTC 2016 i686 i686 i686 GNU/Linux


auser@Integral16gb:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 16.1 GB, 16106127360 bytes
64 heads, 32 sectors/track, 15360 cylinders, total 31457280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x15b82324

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     2140159     1069056    b  W95 FAT32
/dev/sdb2         2140160     4720639     1290240   82  Linux swap / Solaris
/dev/sdb3         4722686    31457279    13367297    5  Extended
/dev/sdb5         4722688    21191437     8234375   83  Linux
/dev/sdb6        21192704    31457279     5132288   83  Linux
auser@Integral16gb:~$ 

sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="3E66E0BE66E077D3" TYPE="ntfs" 
/dev/sda2: LABEL="C_DRIVE" UUID="92BE1EDEBE1EBB25" TYPE="ntfs" 
/dev/sda4: LABEL="RECOVERY" UUID="9CB8910BB890E554" TYPE="ntfs" 
/dev/sda5: LABEL="Win7Page" UUID="006ECBE86ECBD516" TYPE="ntfs" 
/dev/sda6: LABEL="Root_1Tb_64b" UUID="a887a4b0-f168-4dd3-bd76-f39c3f9faf7a" TYPE="ext4" 
/dev/sda7: LABEL="Home_1TB_64b" UUID="1ceaaba3-7868-4b8b-8a7e-97b3f7299e67" TYPE="ext4" 
/dev/sda8: LABEL="terp-transf" UUID="ede17601-b511-4f49-b0e4-bf771aaa467b" TYPE="ext4" 
/dev/sda9: LABEL="1TB_new_root_64b" UUID="80b3f064-07d3-4083-afe0-b4c01237fc41" TYPE="ext4" 
/dev/sda10: LABEL="1TB_new_home_64b" UUID="32a26ba1-4068-4cf4-887e-f587dd9013d2" TYPE="ext4" 
/dev/sda11: LABEL="testroot_1TB_64b" UUID="cc67c044-b996-439e-a158-d80f1e770a3c" TYPE="ext4" 
/dev/sda12: LABEL="testhome_1TB_64b" UUID="869a3318-a0a1-4feb-936e-da1ef028b3e6" TYPE="ext4" 
/dev/sda13: LABEL="newData" UUID="ebb97def-3a7f-4aa2-bf21-b07775b9a3f7" TYPE="ext4" 
/dev/sda14: LABEL="SYSTEM" UUID="3E66E0BE66E077D3" TYPE="ntfs" 
/dev/sda15: LABEL="C_DRIVE" UUID="92BE1EDEBE1EBB25" TYPE="ntfs" 
/dev/sda16: LABEL="Terp-ntfs" UUID="08A4574470F98C79" TYPE="ntfs" 
/dev/sdb1: LABEL="16GB-fat32" UUID="191C-3EF6" TYPE="vfat" 
/dev/sdb2: UUID="225279df-3bb4-4a2d-bf80-6c5d35acec25" TYPE="swap" 
/dev/sdb5: UUID="e0d11933-5042-4025-af6f-7511b3f1798e" TYPE="ext4" 
/dev/sdb6: UUID="24f845cd-87b3-4cc7-a072-752988df3630" TYPE="ext4"

---

### Post by sudodus on 2016-02-11
I may have misunderstood. I thought your computer boots from a USB drive, and that you also want it to boot from Plop in the CD drive chainloading into a USB drive.

If this is correct I think your problem is with the BIOS/firmware system (not with the partition table or file systems or linux). I am sorry, but I do not know much enough to troubleshoot booting via Plop. Maybe someone else who reads this thread knows better and will give you a good reply, but I think the best chance to get help is at the Plop web site. If you are lucky, the developer of Plop might get interested and help you.

[https://www.plop.at/en/contact.html](https://www.plop.at/en/contact.html)
[https://forum.plop.at/](https://forum.plop.at/)

---

