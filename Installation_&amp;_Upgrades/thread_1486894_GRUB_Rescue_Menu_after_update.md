---
title: "GRUB Rescue Menu after update"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by risc12 on 2010-05-18
While I was updating to the newest version of Ubuntu (Lucid?), they asked me something about GRUB. I didn' t knew what to fill in exactly so I marked all options.
Now, after rebooting, I only get the GRUB Rescue Menu. Help command doesn't work. ls gives (hd0) and another one (my cd driver). If i use ls (hd0)/<directory> I get an read error.
Does anyone knows how to fix this?
For further information:
I have one Harddisk in my pc, with three partitions (Windows Vista, Data, and Ubuntu Linux). I used the boot selection function from windows. And now i only have an broken GRUB :(.

I REALLY need help fast!!

Thanks,
Risc12

---

### Post by darkod on 2010-05-18
When you say you used the boot selection from windows, you mean you were using windows boot loader that was calling grub2 for you?

The quick fix I know is installing grub2 to the MBR of the hdd and let it run the boot process. Boot the ubuntu cd in live mode and post the result of:

sudo fdisk -l (small L)

---

### Post by risc12 on 2010-05-18
Yes i do mean the bootloader, but there aint a way to boot rescue-grub

---

### Post by darkod on 2010-05-18
But you can still use ubuntu in live mode right? Boot with the ubuntu cd, and select Try Ubuntu. That will load ubuntu running from the cd.

---

### Post by Tkdboy on 2010-05-18
Ok dont worry...
I had the same problem 2 weeks ago.
You have to use the live cd.
Open ubuntu and install grub2 from the terminal.
Let me find more info for u...
Hold on

---

### Post by Tkdboy on 2010-05-18
Hi...

Look at this links.
Its very easy

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

At the end: look for (Error 15 - File not found)

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by antonic on 2010-05-18
Hi I have the same problem as mentioned. And after doing this command I get this.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23412340

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10195    81780406    7  HPFS/NTFS
/dev/sda3           10196       19457    74397015    5  Extended
/dev/sda5           10196       19178    72155916   83  Linux
/dev/sda6           19179       19457     2241036   82  Linux swap / Solaris

I installed win7 and then ubuntu and when i went for lynx upgrade everything went down. When i try direct boot (without live CD) i get no file error and grub rescue stuff. 

Thx

---

### Post by darkod on 2010-05-18
> **antonic said:**
> Hi I have the same problem as mentioned. And after doing this command I get this.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23412340

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10195    81780406    7  HPFS/NTFS
/dev/sda3           10196       19457    74397015    5  Extended
/dev/sda5           10196       19178    72155916   83  Linux
/dev/sda6           19179       19457     2241036   82  Linux swap / Solaris

I installed win7 and then ubuntu and when i went for lynx upgrade everything went down. When i try direct boot (without live CD) i get no file error and grub rescue stuff. 

Thx

The quick fix would be:

Boot with the ubuntu 10.04 cd into live mode and in terminal execute: (because your ubuntu partition is /dev/sda5 from your results)

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Restart and you should get grub2 menu. If that doesn't work, we'll need more info from your system.

---

### Post by risc12 on 2010-05-18
I don't get any further with the link you provided, so here is the list-l output:
 
   Device Boot      Start            End          Blocks     Id        System
/dev/sda1   *               1       12749    102406311    7  HPFS/NTFS
/dev/sda2           12750      117680   842858257+   7  HPFS/NTFS
/dev/sda3          117681      121601    31495204    f  W95 Ext'd (LBA)
/dev/sda5          117681      121601    31495172+   7  HPFS/NTFS

---

### Post by antonic on 2010-05-18
This worked Darkod. I have my GRUB back. And I am able to boot ubuntu back. But I installed windows7 along (actually before Ubuntu) and I can't get it to boot. When I choose it from GRUB menu it just goes to cursor in top left corner and blinks.

P.S. I am not sure did I do the right thing by installing Windows first. Since all the problems I can see around the different forums are since ppl install Ubuntu first, and then win "eats" GRUB. I did ok here or not?

---

### Post by arrange on 2010-05-18
You installed Grub to the Windows boot sector which you have to repair now.
It's done by the *fixboot* command from a Win recovery CD or via *testdisk* in Ubuntu.

---

### Post by wilee-nilee on 2010-05-18
Carry on.

---

### Post by darkod on 2010-05-18
> **antonic said:**
> This worked Darkod. I have my GRUB back. And I am able to boot ubuntu back. But I installed windows7 along (actually before Ubuntu) and I can't get it to boot. When I choose it from GRUB menu it just goes to cursor in top left corner and blinks.

P.S. I am not sure did I do the right thing by installing Windows first. Since all the problems I can see around the different forums are since ppl install Ubuntu first, and then win "eats" GRUB. I did ok here or not?

You did good, except for one choice. During the upgrade in the window asking where to install grub2, you selected not only the disk(s), but also all partitions. You have to make difference in linux terms /dev/sda, /dev/sdb, etc are disks, and if it has a number it's a partition on that disk.

In most cases, except in exceptions, bootloaders go to the disk (the MBR), NOT on the partitions.

From your fdisk results it seems your win7 boot partition is /dev/sda1. Use these instructions to fix it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to repair partition #1 on /dev/sda.

---

### Post by wilee-nilee on 2010-05-18
Never mind read the OP 1st post.

---

### Post by darkod on 2010-05-18
> **risc12 said:**
> I don't get any further with the link you provided, so here is the list-l output:
 
   Device Boot      Start            End          Blocks     Id        System
/dev/sda1   *               1       12749    102406311    7  HPFS/NTFS
/dev/sda2           12750      117680   842858257+   7  HPFS/NTFS
/dev/sda3          117681      121601    31495204    f  W95 Ext'd (LBA)
/dev/sda5          117681      121601    31495172+   7  HPFS/NTFS

You have no ubuntu partition here. Did you install wubi maybe? It's installed inside windows and doesn't create an ubuntu partition like the full dual boot install.

---

### Post by risc12 on 2010-05-18
I indeed installed Wubi, i totally forgot that! Is there an easier solution? Or is it now impossible to fix?
Thanks

---

### Post by darkod on 2010-05-18
> **risc12 said:**
> I indeed installed Wubi, i totally forgot that! Is there an easier solution? Or is it now impossible to fix?
Thanks

Uhhh... I really don't know what selecting all partitions in that window would do in wubi install. It's not the same as ubuntu install.

Lets see more info about your system, follow these instructions and post the content of your results.txt file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by antonic on 2010-05-18
Darkod u r the man :). I ran testdisk as said in the "tutorial" and I have windows back as well. If u ever get to Croatia (dalmatia actually) I owe you a beer at least :).

Thanks:biggrin:

---

### Post by risc12 on 2010-05-18
Ok, i will do tha later this week. I have to learn for two tests tomorrow, so thursday or friday i will post it.
Very much thanks for your help so far! i can now use my ubuntu live stick if i really need an pc.
Thanks again! The ubuntu community is really awesome!

---

### Post by risc12 on 2010-05-19
Here is the Result.txt:

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1734656 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 1734712 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 1769272 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,812,684   204,812,622   7 HPFS/NTFS
/dev/sda2         204,812,685 1,890,529,199 1,685,716,515   7 HPFS/NTFS
/dev/sda3       1,890,529,200 1,953,519,607    62,990,408   f W95 Ext d (LBA)
/dev/sda5       1,890,529,263 1,953,519,607    62,990,345   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4237 MB, 4237295616 bytes
37 heads, 36 sectors/track, 6213 cylinders, total 8275968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     8,275,967     8,267,776   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       331197b0-92c8-4d11-b1c0-e859947d8529   ext4                                     
/dev/sda1        94A4A125A4A10AB6                       ntfs                                     
/dev/sda2        CEDAF3D9DAF3BC31                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        A0A07967A07944B6                       ntfs       Linux                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4E1B-43AB                              vfat       MYLINUXLIVE                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda5: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/stage2
```I really hope someone can help me out!
I really need windows back, maybe reinstalling the MBR trough testdisk is an idea? I don't want to screw up any data so maybe you can give me some advice! I' m real desperate :confused:.
Oh, and it just crossed my mind that I only need the possibility to boot into Windows, so i can reinstall Wubi, is that correct? I really start to like Ubuntu, but i also really need Windows!

Thanks in advance!

---

### Post by darkod on 2010-05-19
> **risc12 said:**
> I really hope someone can help me out!
I really need windows back, maybe reinstalling the MBR trough testdisk is an idea? I don't want to screw up any data so maybe you can give me some advice! I' m real desperate :confused:.
Oh, and it just crossed my mind that I only need the possibility to boot into Windows, so i can reinstall Wubi, is that correct? I really start to like Ubuntu, but i also really need Windows!

Thanks in advance!

You need to run this fix:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

on both partition #1 and #5 on disk /dev/sda. You can run it on one partition at a time, so you will need to run it twice.
You can run it from ubuntu live mode.

That should bring back windows, and whether wubi will still work inside windows I don't know. Try first, maybe you won't need to reinstall it.

---

### Post by risc12 on 2010-05-19
Well it does not bring back windows :(. But it does bring me the normal grub interface. Testdisk now tells me that the back-up boot sector and the boot sector (for both partitions) are identical. So I tried Rebuild BS, didn't give any changes. What now?
Maybe i should try Repair MTF? Don't have ANY idea what it means, maybe you guys could tell me what it is?

Oh, and if I do Rebuild BS, in sda1 it tells me it is identical, on sda5 it is different, should i try the [write] option?

---

### Post by darkod on 2010-05-19
> **risc12 said:**
> Well it does not bring back windows :(. But it does bring me the normal grub interface. Testdisk now tells me that the back-up boot sector and the boot sector (for both partitions) are identical. So I tried Rebuild BS, didn't give any changes. What now?
Maybe i should try Repair MTF? Don't have ANY idea what it means, maybe you guys could tell me what it is?

Oh, and if I do Rebuild BS, in sda1 it tells me it is identical, on sda5 it is different, should i try the [write] option?

Sorry, my mistake. I overlooked grub2 on the MBR. To get rid of it, execute from live mode:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give. That will write a generic windows mbr on /dev/sda and should start booting the windows bootloader.

Since you have wubi, you are not using grub2. At least not in the first stage. First comes windows bootloader, and then only if you select ubuntu from it, it loads the virtual grub2 from wubi.

---

### Post by risc12 on 2010-05-19
I just rebooted and Windows is alive!! Tomorrow I will test Wubi. Now i need to quit my pc.
Darkod, I want to thank you very very very very much! I will stay active within Ubuntu, Wubi and this community, and i hope that there will be a day I can serve other Ubuntu users with my knowledge!
Goodnight! (here it is 21:35, so in a few hours I go to bed)

---

### Post by tibman on 2010-12-30
I recently had this same problem. Ubuntu crashed so I tried deleting my Ubuntu partition. On restart I found grub unable to load and no access to my windows 7 os. What I did was using gparted, removed ubuntu's ext 4 and swap partition, then expanded my ntfs win 7 partition. Then using the dvd version of Ubuntu 10.10, reinstaled ubuntu using the "along side other operating system option" and presto! Grub restored and windows 7 accessible! :)

---

