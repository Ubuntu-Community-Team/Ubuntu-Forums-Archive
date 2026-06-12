---
title: "Installed successfully, but now &quot;error:no such partition, grub rescue&quot;"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by ianhoolihan on 2010-12-02
Hi all,

Firstly, I'm a complete newbie, trying to get away from Windows Vista! I had some issues installing Ubuntu, but finally got it sorted - so I thought. I wanted to view a dnl file, so tried to boot into Windows, and I got a white screen with big red letters saying "ERROR". So I held down the off button for 5 seconds, and then tried to reboot. But now all I get is the words:

error: no such partition
grub rescue>

Before I go further, I'll summarise the problem with my install. Basically it would only get partway through, if at all, and then all the options would freeze...I could move the mouse, but that was it. Similarly with running Ubuntu on the LiveCD. After a lot of hassle, and some helpful members of the community, it turned out that all I needed to do was use the option "nomodest" when installing, and it all went fine. Well actually I had to retry it again in recovery mode because I think maybe a driver wasn't loaded (?), but after that everything seemed alright.

So as mentioned before, I've come to my present issue. Typing "Is" gives "Unknown command" (or maybe "invalid"...I can't remember). And if I type "set" I get something like "prefix=..." and something else...sorry I can't remember and I don't want to turn off the computer now just in case things don't work again. 

Anyway I managed to boot and run Ubuntu using the LiveCD, and started looking for solutions. Note that I used the "nomodest" option again to boot. Anyway all the solutions involve first using "fdisk -l" to find the partitions. Here is the output:

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1276       11004    78142464    7  HPFS/NTFS
/dev/sda3           11004       38914   224184321    f  W95 Ext'd (LBA)
/dev/sda5           20732       38914   146041856    7  HPFS/NTFS
As you can see, there appears to be no Windows or Linux installed. Also

> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="RECOVERY" UUID="3C98-AC5D" TYPE="vfat" 
/dev/sda2: LABEL="VistaOS" UUID="4C901D9C901D8E18" TYPE="ntfs" 
/dev/sda5: LABEL="DATA" UUID="F8CA203DCA1FF69A" TYPE="ntfs" So it does sort of see it? Anyway when I simply go through "My Computer" as such, I see a 320Gb Hard Disk: DATA, and 320GB Hard Disk: VistaOS and one called File System. Now beforehand, I had my 320GB formatted into 2 partitions, one called DATA, and the other called VistaOS I'm assuming. Then when I installed Ubuntu, I created another partition alongside the one Windows was installed in. It appears that this partition is no longer there. I can however access all my data on the DATA partition, and all my old Windows folders from the VistaOS partition. The File System partition has folders beginning: bin, boot, cdrom, dev, etc, home, lib, media, mnt, opt, proc, rofs, root (this has an X on the icon), sbin, selinuz, srv, sys, tmp, usr, var, and files initrd.img and vmlinuz though these two have X's on the icons. I tried to open the root folder (the one with the X) but it says "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "root"".

That is about all the information I can come up with at the moment, and any help would be much appreciated. I have read that using "nomodest" could be why the partitions are not being recognised, but I fear if I don't use this I may have the same problems when I tried installing, and it will freeze etc. 

So if anyone could give me some advice, that would be great!

Cheers

---

### Post by oldfred on 2010-12-02
To see the entire boot configuration.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

nomodeset relates to video card issues and applies after grub has booted, but before/as Ubuntu boots.

Ubuntu sees LS as different from Ls from ls. Most commands do not use capitals. Also ls (el)  and Is (eye) are often confused (depending on your font). ls is a command, Is is not.

---

### Post by ianhoolihan on 2010-12-02
Thanks oldfred!

Sorry for being so silly and getting my "i"s and "L"s mixed up! Typing in "ls" did give a result, but I forgot to write it down, and anyway I have the following information from your suggestion:

             ```
   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,482,874    20,482,812  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     20,484,096   176,769,023   156,284,928   7 HPFS/NTFS
/dev/sda3         176,771,070   625,139,711   448,368,642   f W95 Ext d (LBA)
/dev/sda5         333,056,000   625,139,711   292,083,712   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        4C901D9C901D8E18                       ntfs       VistaOS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        F8CA203DCA1FF69A                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 b8  50 09 00 d8 68 11 00 00  |........P...h...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```Thank you so much for your help again! Hopefully I'm on the path back to Ubuntu!!

---

### Post by oldfred on 2010-12-02
Grub is trying to boot from sda6, but you do not have one and the sda5 NTFS looks like it goes all the way to the end of the drive.

You either need to shrink the NTFS partition and reinstall or install a windows boot loader in the MBR.

If you did have an install and something reverted the partition table back you may be able to recover with testdisk. But it may be easier just to reinstall.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by ianhoolihan on 2010-12-03
Thanks again oldfred!

I've managed to get into Testdisk, and currently I am running the Deeper search, which is taking a while...so I thought I'd update everyone = )

The quick search gave me three partitions (what follows is not copied and pasted, but was written on paper, so may not be all of it):
1. ```
*FAT32 LBA [RECOVERY]
has 10482MB/10001MiB written
This contains folders like BOOT.SDI, BOOTMGR, IMAGEX.EXE, Wimscript.ini, WINRE.WIM, BOOT, EFI, and the dates are all 2008 or so, which was when I got the computer. 
```So this makes me think it is part of Windows system. The Recovery partition?

2.```
 P HPFS - NTFS 1275  0  1  20730  254  63 312560640
has 160Gb/149Gb written.
When I try to open the files it says "Can't open filesystem. Filesystem seems damaged".
```3. ```
P FAT32 LBA 20731  0  1  23411  254  63  43070265 [NO NAME]
has 22GB/20GiB written
has really weird file names in it like
-r-xr-xr-x  0  0  338554333  13-Jan-1996  18:13 M-ojt..~J~^T
```Since I believe I originally had a 320GB hard-drive formatted into a 160GB DATA drive, and then a Vista C drive, then I'm guessing that #1 corresponds to the recovery Windows partition (11GB out of the 160GB C), and then that #2 corresponds to the remainder of the C drive (149GB). Then #3 should be the DATA drive...I don't understand why it doesn't say 160GB, or why the files are messed up though. Actually looking through the Ubuntu places, the DATA drive still exists. Last time, I could open it and the files were fine. Now I get an error "Error mounting: mount exited with exit code 21: fuse: mount failed: Device or resource busy" which I presume is because I am using Testdisk at the moment? The other drives in Ubuntu are the one called "VistaOS" which I could previously open, and also one just called "File System" which appears to be Linux related (I can still open this one while Testdisk is running).

Since I also installed Ubuntu onto the old C drive, by partitioning it beside the Windows bit, then I think it makes sense that #2 is the damaged one. Hopefully I will be able to recover the Windows and Ubuntu partitions of this drive using Testdisk. I guess if it finds them, I'll cross that bridge when I get to it, but I'm thinking I may need to change the type of each drive etc.

Lastly oldfred, will this be simpler if I just get rid of Windows completely? As before, I can access all my old documents, so I'm actually fine with getting rid of Windows. Going cold-turkey will be good for me! I was actually almost about to get rid of the Windows before everything went wrong, as I realised I had nearly everything I needed on Ubuntu...hence I was wondering if it was possible to keep the Ubuntu system I had installed (and the programs I downloaded etc), or will I need to reinstall Ubuntu?

Ok, Deep Seach is 34% through, and has found another partition called Linux...yay! 

I will update you when finished...is there any way to save all the results of testdisk so I can give them to you guys?

Cheers once again!!

---

### Post by oldfred on 2010-12-03
I have only gone out to look at testdisk as I never had to actually run it.

I think you could copy it to a file and save to a flash drive. But I do not know how to read it. Others may. Some have been able to recover partitions but you have to review and make sure they do not overlap. They may or may not then be correct. Good Luck

---

### Post by ianhoolihan on 2010-12-03
Thanks for the advice again oldfred!

Before I begin, I just  remembered something. When I first tried to boot Windows with grub,  there were two options for Windows: on sda1 and sda2 (or something like  that). I think (with the foggiest recall) that I chose sda2...?

Anyway, I've run the Deep Search, and here's the link for the log file: [http://pastebin.ubuntu.com/539510/](http://pastebin.ubuntu.com/539510/)

I've  also included some of my own stuff, and we'll see if my detective work  is on the mark - I hate to say it, but I'm actually kind of enjoying  figuring this out...except that I need the computer to do my work on!

OK, so the results of the deep search:

```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
1#* FAT32 LBA                0   1  1  1274 254 51   20482800 [RECOVERY]
D HPFS - NTFS           1275   0  1 20730 254 63  312560640
2#D HPFS - NTFS           1275  19 25 11003  92 26  156284921 [VistaOS]
3#D HPFS - NTFS           1275  19 25 20731 165 42  312569856 [VistaOS]
4#D Linux                         11003 125  3 20329 210 41  149827584
D Linux                         15460  67 32 24786 153  7  149827584
D Linux                         15461  40  4 24787 125 42  149827584
D Linux                         15468 140 33 24794 226  8  149827584
D Linux                         15472  63 16 24798 148 54  149827584
D Linux                         15473   3 19 24799  88 57  149827584
D Linux                         15474   8 23 24800  93 61  149827584
5#D Linux Swap               20329 243 11 20731   2 55    6442992
D FAT32 LBA              20731   0  1 23411 254 62   43070264 [NO NAME]
D HPFS - NTFS          20731   1  1 38912 254 63  292093767
6#D HPFS - NTFS          20731 198 12 38913  37 36  292083712 [DATA]
```Now,  if my memory serves me correctly, those I have marked with # all showed  files, except for #5, which wouldn't show anything (it didn't say  "damaged files" like the rest either). From the files and sizes, and the  start/end points, my guesses are as follows:

#1 Windows recovery partition that was originally there
#3 My "C" drive that was originally there, that I installed Ubuntu on, alongside Windows.
#2 The new Windows partition
#4 The new Linux partition
#5 I think this is like the Linux recovery partition maybe?
#6 My original DATA drive.

So  I'm thinking the solution is to change the drive types, but how I'm not  sure. Firstly I'm not sure which one to make the bootable (*) drive.  Secondly, I would think #3 should be the extended drive, but testdisk  won't give me that option. Thirdly I'm guessing that #2, #4, #6 should  be marked as L(ogical), but I don't know the difference between primary  and logical, so could be wrong here.

Also I'm not sure what the  partition "NO NAME" is, because it is recognised in the quick search,  but when I open it, it is full of unrecognisable files, with weird names  etc, such as -r-xr-xr-x  0  0  338554333  13-Jan-1996  18:13  M-ojt..~J~^T.

Lastly, I'm not actually too worried about losing  Windows accessibility. I managed to access all my old documents last  night and back them all up, so in that sense I'm fine. Sure, it'd be  nice to have the option of Windows if I ever needed it, but part of me  really likes the idea of going cold turkey! Just so long as Ubuntu  continues to work = ).

Thanks once again everyone - what an awesome community!

---

### Post by oldfred on 2010-12-03
Linux swap is the memory overflow area for when applications use more than your RAM, it is also used for hibernation. If you have lots of RAM it may not have even been used.

It looks like the names shown are labels that you can (should) add to partitions to help identify them. Not sure why you would have a no name but perhaps somewhere in resetting things it got added.

I think I have seen several cases where users clicked on the windows recovery partition and the partition table gets messed up. Not sure if it starts to install or just because it does not see/know what a Linux partition is "corrects" the partition table.

---

