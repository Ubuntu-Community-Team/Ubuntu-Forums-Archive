---
title: "Reinstalling grub"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by nynamyna on 2011-03-31
Hello everybody,

I am new to ubuntu. I had ubuntu 10.04 for sometime in my laptop. I had a separate drive for windows and I was using windows virtually in that. Now i wanted to create a dual boot so, I went and formatted, installed windows in the drive in which I had windows virtually (I used windows cd to boot). After that I was able to boot to windows not ubuntu (The boot menu did not appear). So I went and tried the following tutorial for installing Grub2

[https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands](https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands)

It said that install completed with no errors. But now, I am getting 

error: file not found.
Grub rescue >

Now I am not able to boot to either windows or Ubuntu

Thanks,
Vijay

---

### Post by coffeecat on 2011-03-31
I think you were looking in the wrong part of that documentation page. This is what you needed:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Anyway, boot up with the live Ubuntu CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the bootscript and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags as described in that link. Then we will be able to see what is on your system and what needs to be done.

---

### Post by Rubi1200 on 2011-03-31
+1 for the boot info script recommended by coffeecat; it will really help us help you.

Alternative instructions:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by nynamyna on 2011-03-31
I am not able to connect to the internet.can we download this and put in a pen drive

---

### Post by coffeecat on 2011-03-31
> **nynamyna said:**
> I am not able to connect to the internet.can we download this and put in a pen drive

Yes, no problem. Once you've downloaded it and copied it to the pendrive, boot up the live CD, insert the pendrive and copy the boot_info_script*.sh file to the live desktop. Then follow Rubi1200's instructions.

---

### Post by nynamyna on 2011-03-31
```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 326135565.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   326,133,759   326,131,712   7 HPFS/NTFS
/dev/sda2         326,135,565   530,932,184   204,796,620  83 Linux
/dev/sda3         530,937,854   608,395,263    77,457,410   5 Extended
/dev/sda5         605,124,608   608,395,263     3,270,656  82 Linux swap / Solaris
/dev/sda4         608,397,615   625,137,344    16,739,730  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7998 MB, 7998537728 bytes
5 heads, 32 sectors/track, 97638 cylinders, total 15622144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,064    15,622,143    15,614,080   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B2E893C0E8938171                       ntfs                                     
/dev/sda2        2A57-FEB5                              vfat       New Volume                    
/dev/sda3: PTTYPE="dos" 
/dev/sda4        8bb39532-f0af-46c5-9141-96b13b6b5507   ext3                                     
/dev/sda5        6ab3c4d2-0a7d-4917-aec2-f0a0c23ac074   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0E00-0AA5                              vfat       RAMANAN AV(                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/RAMANAN AV(       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  65 d6 c5 ad 8c b7 ba 97  63 d0 38 c0 78 06 2a d3  |e.......c.8.x.*.|
00000010  84 cc 0a ff fb 92 00 e7  08 02 f3 66 54 13 07 13  |...........fT...|
00000020  70 60 2c da c7 3c 45 6f  4b d5 9b 5d 47 8c 6d e1  |p`,..<EoK..]G.m.|
00000030  82 33 2c b4 c1 8d bd 9f  a4 63 90 34 74 bb 1e 39  |.3,......c.4t..9|
00000040  12 21 72 8e 28 18 6b a2  55 bf bb ba 9f f1 8f fb  |.!r.(.k.U.......|
00000050  3c 5d 6d 0d ae c8 cd ea  73 80 90 c8 09 71 40 c4  |<]m.....s....q@.|
00000060  68 81 00 02 b7 83 b3 22  00 40 00 b1 0d 30 46 49  |h......".@...0FI|
00000070  59 ab 0c bf 14 1d 0c d9  bb ba b1 e6 52 ad 35 25  |Y...........R.5%|
00000080  72 98 d0 70 87 60 eb 7b  65 53 f3 14 c6 20 cf e1  |r..p.`.{eS... ..|
00000090  9b 2e b6 2d 6c 65 bd d4  bb 1e 81 c6 03 c0 31 56  |...-le........1V|
000000a0  9c 26 60 54 fd 23 1c 80  18 e9 76 3c 72 24 42 e5  |.&`T.#....v<r$B.|
000000b0  1c 50 30 d7 44 a2 ef ee  ee a7 fc 63 fe cf 17 58  |.P0.D......c...X|
000000c0  f3 2b 76 3a 3a 32 da 26  a2 00 8b 24 15 40 93 15  |.+v::2.&...$.@..|
000000d0  e1 ec 03 98 73 a8 e3 2a  e4 3b dc 97 65 31 25 6a  |....s..*.;..e1%j|
000000e0  24 8a f6 43 07 6f 99 be  9b 6f 0a 2b c0 42 eb 08  |$..C.o...o.+.B..|
000000f0  45 64 3d dd c4 67 7f 4f  de f6 f3 76 23 19 0b bd  |Ed=..g.O...v#...|
00000100  5d 36 5b f8 3e 0a 08 8d  c2 e6 ef 32 61 a9 43 a4  |]6[.>......2a.C.|
00000110  05 12 2a 7d d3 f4 dd be  ab bf ff ff e3 43 99 5b  |..*}.........C.[|
00000120  b1 d1 d1 96 d1 35 10 04  59 20 aa 04 98 af 0f 60  |.....5..Y .....`|
00000130  1c c3 9d 47 19 57 21 de  e4 bb 29 89 2b 51 24 57  |...G.W!...).+Q$W|
00000140  b2 14 3b 7c cd f4 db 78  51 5e 00 03 62 10 99 25  |..;|...xQ^..b..%|
00000150  77 74 42 ee d7 ae 6e 46  68 85 04 3b 98 ed 09 ee  |wtB...nFh..;....|
00000160  81 d0 a0 88 dc 2e 6e f3  26 1a 94 3a 40 51 22 a7  |......n.&..:@Q".|
00000170  dd 3f 4d db ea bb ff ff  fe 35 88 00 00 2f 66 b6  |.?M......5.../f.|
00000180  e9 16 64 2e a1 30 88 94  3c a0 f8 17 ce ce b6 37  |..d..0..<......7|
00000190  50 d9 e8 c6 7f 96 ed 5e  05 2f 4d db 7b 83 9f 5e  |P......^./M.{..^|
000001a0  98 2f c7 ff 2a 66 c0 13  96 f4 e9 53 3b 25 3d 29  |./..*f.....S;%=)|
000001b0  9d a7 8b 1c 0d ff fb 92  00 e7 0c c3 5b 24 00 fe  |............[$..|
000001c0  ff ff 82 fe ff ff 02 00  6c 04 00 e8 31 00 00 00  |........l...1...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by coffeecat on 2011-03-31
Your boot script output shows that grub in the mbr is looking in partition sda1 for /boot/grub. But sda1 is your Windows partition, so that won't work. Unfortunately, there is no detectable Ubuntu system on the drive. Partition sda4 is formatted ext3 but has no operating system in it - according to boot script. 

Another thing is that there is approximately 38GB unallocated in your extended partition. It contains only one swap partition (sda5) which is approx 1.7GB. I suspect that the Windows 7 installer has erased your Ubuntu root partition. I was doing some experiments with both the XP and Vista installers and the Vista installer erased a Linux logical partition in a very similar partition layout. This is a problem with Windows installers when logical partitions formatted with Linux filesystems are present.

I have a couple of suggestions.

1 - You can repair the mbr with Windows code to get yourself booting into Windows. This will not affect the next suggestion and will at least make the machine usable for now.

2 - You can run testdisk from the live CD to see if it can detect and restore the erased Ubuntu partition - assuming my suspicion is correct. The partition and filesystem are hopefully still intact - simply that the partition table entry needs restoring.

3 - Once (and if) testdisk has restored you Ubuntu partition, then you can use the link I provided above to re-install grub.

If you need any help with that, then post back.

---

### Post by oldfred on 2011-03-31
I see two issues. One is part of grub installed to your windows that will prevent windows from working and sda2 in one place say FAT and the other type 83 linux.

You need to delete the /boot in windows but be careful not to delete the /Boot as it has essential boot file BCD in it. Windows is not case sensitive so it cannot handle  /Boot & /boot as to it they are the same.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Then you can put windows into the MBR and boot windows if you want.

The issue on sda2 may be just corruption. I might try e2fsck, but do not know if it will see it as an ext or FAT partition.

From liveCD so everything is unmounted,swap off if necessary, change sda2 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda2
if errors:
sudo e2fsck -f -y -v /dev/sda2

---

### Post by nynamyna on 2011-03-31
@coffeecat: Thank you very much for your suggestions. I am out now. i will try them and post here. Which method you suggest me to use in the link you have given?

@oldfred: I will first delete the folder /boot using the live cd

how to do this "Then you can put windows into the MBR and boot windows if you want." ?

---

### Post by coffeecat on 2011-03-31
> **oldfred said:**
> One is part of grub installed to your windows that will prevent windows from working and sda2 in one place say FAT and the other type 83 linux.

Yes, I missed those. 

@nynamyna, oldfred is quite right. However, I'm still deeply suspicious about the 38GB unallocated space in your extended partition, bearing in mind Windows installers' proven track record in causing havoc in partition tables with Linux logical partitions. Do you recall whether there was free space in your extended partition before you installed Windows? Or did you have more than one partition? If you did, then you need to bear  in mind that there could be a missing partition.

---

### Post by nynamyna on 2011-03-31
@Coffeecat: no i didn't have so much free space before. So is the root partition got erased ? I had three partitions

1. A partition with linux
2. A partition for about 100 gb 
3. a partition for 8.5 gb
4. a partition in which i was running windows virtually which was about 155gb i think...

---

### Post by coffeecat on 2011-03-31
> **nynamyna said:**
> @Coffeecat: no i didn't have so much free space before. So is the root partition got erased ? 

I don't know, but we need to investigate that 38GB free space.

I think you need to concentrate on the issues that oldfred identified first. You need to remove the /boot folder in sda1 that contains grub code with the method that oldfred posted a link to. You can do this with the Ubuntu live CD since you can't boot into Ubuntu on the hd. Be sure to read that link carefully and delete the /boot folder, not the /Boot folder.

If that was my system I would choose to reinstall the Windows mbr next. Is that Windows 7 or Vista you have? Whichever, you can fix the mbr from the installation DVD with 'bootrec /FixMbr'. See:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Then you might want to investigate whatever is going on with sda2.

Finally, and again if this was my system, I would see if testdisk could find a lost partition in the free 38GB. Since you can't connect to the internet with the live CD, you can't install testdisk to the live Ubuntu session, so apologies for suggesting that before. What you can do is to acquire one of a number of live CDs that include testdisk. Examples:

 [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

But I would leave testdisk to last.

However, see what oldfred and Rubi1200 suggest. This is a complex situation and you need different perspectives.

---

### Post by oldfred on 2011-03-31
Coffeecat is correct. 

When I said you can install windows to the MBR, that is a windows boot loader just to get you able to boot windows if you want. You need a windows repair disk to do that. (Or install a lilo bootloader that will boot windows.) But then to boot Ubuntu you would have to reinstall grub2 to the MBR, but we have to find your Linux partition. Not sure if it is just sda2 or the empty space coffeecat is discussing.

Also coffeecat is correct that we have seen lots of issues with windows rewriting partition tables with incorrect info. Testdisk has been our standard suggestion for fixing many partition issues, but it has sometimes written the end beyond the end and created another issue. Testdisk is usually good at finding the history of old partitions and letting you recover them.

But there is another new tool for fixing missing partitions.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I think it would also tell if your missing space is/was a partition. Not sure if it would also resolve the confusion your system has on partition type for sda2.

---

### Post by srs5694 on 2011-03-31
> **oldfred said:**
> But there is another new tool for fixing missing partitions.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I think it would also tell if your missing space is/was a partition. Not sure if it would also resolve the confusion your system has on partition type for sda2.

FixParts doesn't recover partitions that are missing in the same sense that TestDisk does. TestDisk goes out and scans the disk for filesystem "signatures" and, when it finds one, builds a partition around it. FixParts, by contrast, just fixes mis-sized extended partitions, removes stray GPT data, and enables you to switch partition types from primary to logical or vice-versa. Some of the problems that FixParts handles can make GParted and other libparted-based tools incorrectly report that the disk is empty, but it's not; the "empty disk" report is a libparted bug. The partitions are still defined, and many utilities, including Linux's fdisk, will see them.

Overall, from what I've seen in this thread, I don't think FixParts will be of any help, with one exception: My suspicion is that /dev/sda2 contains a FAT filesystem but is mis-labelled in the partition table as being a Linux partition. FixParts can change partition type codes, so it could change the type code of /dev/sda2 to 0x0C (which is probably correct); however, Linux's fdisk utility can do this, too, and I'd recommend using fdisk for this job rather than FixParts, since FixParts will interpret and re-write the partition table in ways that are likely to be harmless but could cause more problems. The FixParts Web page provides more details on this issue.

---

### Post by nynamyna on 2011-03-31
Thank you guys....I am able to boot into windows now. Now I am downloading the test disk version now. 

@srs5694: can you please tell me how to run fdisk ?

---

