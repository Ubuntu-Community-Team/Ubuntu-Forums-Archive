---
title: "error booting"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by obengsn on 2010-06-28
i have mistakenly deleted a partition to create space after uninstalling Ubuntu. now my computer says

GRUB loading.
error: no such partition
grub rescue>

i am a newbie and have no idea how to get to win 7

somebody pls help

---

### Post by Rubi1200 on 2010-06-28
Hi,
first of all if you have the Ubuntu CD you can use it to boot the computer. Follow the instructions here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and post back to the forums and hopefully someone can help you resolve this problem.

Good luck!

---

### Post by lolzwut on 2010-06-28
You deleted the grub. Boot into windows using the CD and reinstall the MBR. I'm pretty sure you can do it with easyBCD, someone correct me if I'm wrong.

---

### Post by wilee-nilee on 2010-06-28
> **lolzwut said:**
> You deleted the grub. Boot into windows using the CD and reinstall the MBR. I'm pretty sure you can do it with easyBCD, someone correct me if I'm wrong.

The second post is the best advice.

---

### Post by obengsn on 2010-06-28
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,482,874    20,482,812  27 Hidden HPFS/NTFS
/dev/sda2    *     20,484,096   874,873,683   854,389,588   7 HPFS/NTFS
/dev/sda3         874,883,835 1,465,144,064   590,260,230   5 Extended
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B8DC4D2DDC4CE6EA                       ntfs       PQSERVICE                     
/dev/sda2        B8528B27528AEA08                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by wilee-nilee on 2010-06-28
If you don't have a install dvd, here is a recovery disc link.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Just follow the http link to get to see the path to the repair options and run the highlighted command. Save the whole set though this is a important set to have in case of other problems.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I Think you also have the extended partition from the Ubuntu install on there, it can be removed from the disk manager in W7 and the main partition can be expanded.

---

### Post by obengsn on 2010-06-28
> **wilee-nilee said:**
> If you don't have a install dvd, here is a recovery disc link.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Just follow the http link to get to see the path to the repair options and run the highlighted command. Save the whole set though this is a important set to have in case of other problems.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I Think you also have the extended partition from the Ubuntu install on there, it can be removed from the disk manager in W7 and the main partition can be expanded.
i am going to go through step by step. one problem my system is x64 but i only have x32 win 7 will it make any difference?

---

### Post by wilee-nilee on 2010-06-28
> **obengsn said:**
> i am going to go through step by step. one problem my system is x64 but i only have x32 win 7 will it make any difference?

If your install is 32 bit download the 32 bit version. And note you only have to run the bold command, you wouldn't hurt anything with the others probably but just run the fixmbr.

I'm not sure if the rebuild function will work without a actual install dvd.

---

### Post by obengsn on 2010-06-28
what do i do after BootRec.exe /fixmbr ?
it says "the operation completed successfully."

---

### Post by wilee-nilee on 2010-06-28
> **obengsn said:**
> what do i do after BootRec.exe /fixmbr ?
it says "the operation completed successfully."

Reboot it should boot in to W7. I forget exactly how you do it from there though.

---

### Post by obengsn on 2010-06-28
it worked, you are so awesome. i have been on this for 25hrs straight. thanks so much.
how do i use the extended part of the HD?

---

### Post by obengsn on 2010-06-28
you are so awesome. it worked. thank you for saving me from entering the 28th hr working on this.
thank you.
how do i remove the extended partition from the Ubuntu install on there.

---

### Post by wilee-nilee on 2010-06-28
> **obengsn said:**
> it worked, you are so awesome. i have been on this for 25hrs straight. thanks so much.
how do i use the extended part of the HD?

in the start panel type disk manager or disk management I forget, this will take you to the partitioner. I think you still have a partition in there that is called extended in Linux, but has another name in ms. If it is there it is blocking the expansion, so make sure it is empty and delete it then right click or click on your main partition and there is a function to expand or shrink choose expand and It probably does a check but that is the basic idea.

You could also build another ntfs partition there to store stuff if you want, like music...etc

Just remember in the future if you install Linux or another OS always put the bootloader back in before you remove the OS.

---

### Post by obengsn on 2010-06-28
that is what started all this so this time pls hang on, let me restart and make sure it works fine. but thanks you are still awesome.

---

### Post by obengsn on 2010-06-28
oh yeah do i have to change the boot file in bios back to the hard drive??

---

### Post by wilee-nilee on 2010-06-28
> **obengsn said:**
> oh yeah do i have to change the boot file in bios back to the hard drive??

I would, there is also a key prompt to have a choice of what to boot from that is outside of the bios. So in the future if you have the HD first in bios you can hit a f key of some sort or esc and choose to boot from a thumb or cd or whatever else. You will have to figure that one out.

---

### Post by obengsn on 2010-06-28
cool thank you for your help.

---

### Post by wilee-nilee on 2010-06-28
> **obengsn said:**
> cool thank you for your help.

Hey glad it worked out and now you know the method.

---

