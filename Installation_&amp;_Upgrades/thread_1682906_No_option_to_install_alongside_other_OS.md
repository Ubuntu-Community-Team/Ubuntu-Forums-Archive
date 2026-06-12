---
title: "No option to install alongside other OS"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by spudbynight on 2011-02-06
I am trying to install Ubuntu 10.10 on a laptop I have. The laptop is already running Windows 7. I have looked into dual booting and everything I have seen refers to an option to install alongside other OS when installing.

When I try and install I don't have this option. Am I missing something?

---

### Post by s.v.z on 2011-02-06
Well, you can try to assign the partitions manually. Read this article carefully, it may be of some use: [http://www.techhamlet.com/2010/05/how-to-install-ubuntu-10-04/](http://www.techhamlet.com/2010/05/how-to-install-ubuntu-10-04/)

P.S I`d recommend you to resize partitions using Windows programs like Acronis Disk Director. They are much faster than, for example, gparted.

---

### Post by TBABill on 2011-02-06
You may also want to defrag the Windows partition before hand.

---

### Post by presence1960 on 2011-02-06
You want to look in Windows disk management. If you have 4 primary partitions that is one reason the install alongside option will not present itself. if this is the case you are going to have to remove a partition to make room for ubuntu, shrink C: from windows disk management, then from gparted create an extended partition with a minimum of a logical partition for ubuntu and a swap partition. Then select "choose partitions manually" at the installer window and proceed to install to those partitions.

---

### Post by Mark Phelps on 2011-02-07
Presuming your PC can boot from a CD, BEFORE you do anything else, go into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You will need this if problems develop with the Win7 boot loader during your multi-boot setup.

---

### Post by ajapp on 2011-02-08
> **presence1960 said:**
> You want to look in Windows disk management. If you have 4 primary partitions that is one reason the install alongside option will not present itself. if this is the case you are going to have to remove a partition to make room for ubuntu, shrink C: from windows disk management, then from gparted create an extended partition with a minimum of a logical partition for ubuntu and a swap partition. Then select "choose partitions manually" at the installer window and proceed to install to those partitions.

Hi presence1960. Could you detail a little bit more? I'm having the same problem. I have purchased an Asus netbook and it came already with 4 primary partitions. One with win7, one with asus' express gate, one really small (20MB) with something I don't know, and one with free space (117GB). Can I delete this 117GB one and then launch the Ubuntu 10.10 installer and tell it to create its partitions there (boot, swap, /home and /)? Or do I first need to create an extended partition on this unallocated space before going to the ubuntu installer?

Thanks for the help!

---

### Post by presence1960 on 2011-02-08
> **ajapp said:**
> Hi presence1960. Could you detail a little bit more? I'm having the same problem. I have purchased an Asus netbook and it came already with 4 primary partitions. One with win7, one with asus' express gate, one really small (20MB) with something I don't know, and one with free space (117GB). Can I delete this 117GB one and then launch the Ubuntu 10.10 installer and tell it to create its partitions there (boot, swap, /home and /)? Or do I first need to create an extended partition on this unallocated space before going to the ubuntu installer?

Thanks for the help!

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by ajapp on 2011-02-09
Hi presence1960
OK, there you go!
thanks!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,717,248   241,174,527    31,457,280  1b Hidden W95 FAT32
/dev/sda3         241,174,528   488,355,839   247,181,312   7 HPFS/NTFS
/dev/sda4         488,355,840   488,397,167        41,328  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337536 bytes
12 heads, 4 sectors/track, 163669 cylinders, total 7856128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          1,096     7,856,127     7,855,032   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0EC0E05AC0E04993                       ntfs                                     
/dev/sda2        86F4-D40A                              vfat       &#153;&#152;&#153;&#152;&#136;&#136;&#136;&#153;&#152;&#136;&#152;                   
/dev/sda3        1E784E3B784E1247                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        521B-0713                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 32 04  |.X.SYSLINUX...2.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 48 04 00 00  |........?...H...|
00000020  b8 db 77 00 e7 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 13 07 1b 52 4e  4f 20 4e 41 4d 45 20 20  |..)...RNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 08 40 00 00  66 ba 00 00 00 00 bb 00  |}.f..@..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by presence1960 on 2011-02-09
Looks like your sda1 is windows, sda2 is recovery partition, sda4 I would leave alone also even though it may be unnecessary.

What is on sda3? Is that the empty partition you mentioned. If it is I would boot the ubuntu Live CD/USB. Choose "try ubuntu." When the desktop loads go System > Administration > Gparted Partition Editor. Use gparted to delete the sda3 primary partition. Click Apply at top (green check mark). When deleted create an extended partition from all the unallocated space you just made. Click apply. When completed create a logical ext4 partition inside the extended (about 20 GB should be plenty for ubuntu OS). Click apply. When that is done create a swap partition at least as large as your installed RAM. This will allow you to hibernate. If you have a good deal of RAM swap isn't really necessary. The filesystem type will be linux-swap.

The rest of the space in the extended partition I would create a logical NTFS partition for shared file between ubuntu & windows. Click apply. You can now proceed with the install. You just need to choose manual or choose partitions manually at the partitioner window of the ubuntu installer. If you get stuck there post back.

---

### Post by ajapp on 2011-02-09
Yes, sda3 is the empty partition I mentioned before.

So where will be my /home partition if I use this method? Will it be in the new NTFS partition I create? I wanted to be as isolated from Windows as possible, just in case it crashes or gets a virus. So I was thinking of using the rest of the space from sda3 for the Ubuntu /home.
I was reading this tutorial [http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/2/](http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/2/) and they tell you to create 4 partitions using the Ubuntu installer. Is there any need for a "/boot" partition?
Is it safer to create the partitions using gparted or the installer?

Please excuse my questions-overload!

---

### Post by presence1960 on 2011-02-09
> **ajapp said:**
> Yes, sda3 is the empty partition I mentioned before.

So where will be my /home partition if I use this method? Will it be in the new NTFS partition I create? I wanted to be as isolated from Windows as possible, just in case it crashes or gets a virus. So I was thinking of using the rest of the space from sda3 for the Ubuntu /home.
I was reading this tutorial [http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/2/](http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/2/) and they tell you to create 4 partitions using the Ubuntu installer. Is there any need for a "/boot" partition?
Is it safer to create the partitions using gparted or the installer?

Please excuse my questions-overload!
No need for a /boot partition in most cases. If you want a /home partition make the partition I said to use for sharing ext4 instead of NTFS.

When you do the install and choose manual or choose partitions manually you will highlight the ext4 partition for ubuntu OS and click change or edit depending on which version of ubuntu you are installing. On "use as" make sure ext4 is selected. For mount point use the drop down box to select " / "

Then highlight the partition for /home, click change or edit. On "use as" make sure ext4 is selected, and select "/home" for mount point. Then proceed with the install. No need to tick the format box in either as these were just formatted as ext4.

---

### Post by ajapp on 2011-02-09
Thanks! I'll give it a try and post the result back here!

---

### Post by presence1960 on 2011-02-09
> **ajapp said:**
> Thanks! I'll give it a try and post the result back here!

OK I'll check back later

---

### Post by ajapp on 2011-02-09
> **presence1960 said:**
> OK I'll check back later

Gparted quits unexpectedly right after I start it and it's searching my drive.
Already tried to use another USB stick and the same error occurs. Also checked my .iso with MD5SUM and it's ok. Used universal-usb-installer-1.8.2.0 to create the usb.
Don't know what to do next. Can I delete the partition on windows, run the ubuntu installer and tell it to install in the unallocated space?
Thanks!

---

### Post by oldfred on 2011-02-09
I had gparted stop working on my sda drive, but saw sdb, & sdc. sda was my XP install and it was working. After I did a chkdsk on the NTFS partition then gparted would see sda.

I would try running chkdsk from windows on your NTFS partition(s).

---

### Post by presence1960 on 2011-02-09
> **ajapp said:**
> Gparted quits unexpectedly right after I start it and it's searching my drive.
Already tried to use another USB stick and the same error occurs. Also checked my .iso with MD5SUM and it's ok. Used universal-usb-installer-1.8.2.0 to create the usb.
Don't know what to do next. Can I delete the partition on windows, run the ubuntu installer and tell it to install in the unallocated space?
Thanks!

That should work, but give oldfred's suggestion a go first.

---

### Post by remudi on 2011-02-10
i also have this problem. so i asked a youtuber that specifies in ubuntu and he also had no idea when he told me to send him a picture of my gparted. As you can see theres some sort of error alert next to my windows harddrive/partition. this is what it looks like

---

### Post by presence1960 on 2011-02-10
> **remudi said:**
> i also have this problem. so i asked a youtuber that specifies in ubuntu and he also had no idea when he told me to send him a picture of my gparted. As you can see theres some sort of error alert next to my windows harddrive/partition. this is what it looks like

I have never seen that before. Did you at least try resizing the partition with gparted? If it does not work try using windows disk management utility to shrink C:

---

### Post by oldfred on 2011-02-10
If you click (right click?) on the error symbol in gparted it may give you some more info about what the error is. It just may be saying the partition has issues and you need to run chkdsk.

---

### Post by ajapp on 2011-02-11
I ran chkdsk, and gparted still wouldn't work.
So I just deleted the partition with windows disk manager and installed ubuntu with 5GB swap and the rest for "/". Seems  to work great! After installing the drivers my wireless is working and I'm now downloading the over 200 upgrades!

Thanks for your help!

---

### Post by stchman on 2011-02-11
> **spudbynight said:**
> I am trying to install Ubuntu 10.10 on a laptop I have. The laptop is already running Windows 7. I have looked into dual booting and everything I have seen refers to an option to install alongside other OS when installing.

When I try and install I don't have this option. Am I missing something?

I ran across this when installing 10.10.  Since I upgrade releases on my laptop every so often, I put all my data on another partition.  All I have to do is then wipe the partition that contains the OS and my data is preserved.

Well, it looks like 10.10 has a different idea.  Luckily there is the alternate .iso.

[http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

In the alternate version there is the option to use largest continuous free space.  Why the developers found it necessary to remove that.  Also, the alternate CD takes a LOT LONGER to install.

---

### Post by presence1960 on 2011-02-11
> **ajapp said:**
> I ran chkdsk, and gparted still wouldn't work.
So I just deleted the partition with windows disk manager and installed ubuntu with 5GB swap and the rest for "/". Seems  to work great! After installing the drivers my wireless is working and I'm now downloading the over 200 upgrades!

Thanks for your help!

You are welcome, enjoy ubuntu!

---

