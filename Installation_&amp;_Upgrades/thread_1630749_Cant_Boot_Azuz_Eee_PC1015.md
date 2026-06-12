---
title: "Cant Boot Azuz Eee PC1015"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by DeanG on 2010-11-25
My first attempt at seeking help has not been very successful.  Probably to much of a narrative.  If you want to know How I got in this mess see my first post.

Machine: Asus Eee PC 1015

What I know:  I can't boot into anything but Live USB

What I think:  
[LIST]
[*]Win7 starter is still there
[*]Mint9 is lurking as well
[*]Vista recovery partition exists
[/LIST]

What I don't have: 
[LIST]
[*]External USB DVD or CD drive
[*]Win7 Recovery
[/LIST]

What I need:  HELP!

[http://usa.asus.com/product.aspx?P_ID=FDCHJHBkPJpq6YVA](http://usa.asus.com/product.aspx?P_ID=FDCHJHBkPJpq6YVA)

[CODE]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
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
    Boot files/dirs:   /bootmgr /boot/bcd /boot/grub/core.img

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

/dev/sda1               2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2    *    209,717,248   241,174,527    31,457,280   b W95 FAT32
/dev/sda3         241,174,528   488,355,839   247,181,312   7 HPFS/NTFS
/dev/sda4         488,355,840   488,397,167        41,328  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907711 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            129     3,907,007     3,906,879   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       457fac37-64ea-f04d-a1e6-d446f273cd7d   ext2       casper-rw                     
/dev/sda1        0420358A20358428                       ntfs                                     
/dev/sda2        86F4-D40A                              vfat                                     
/dev/sda3        1E784E3B784E1247                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D85C-ED80                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 81 00 00 00  |........?.......|
00000020  3f 9d 3b 00 e0 0e 00 00  00 00 00 00 02 00 00 00  |?.;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 80 ed 5c d8 4e  4f 20 4e 41 4d 45 20 20  |..)..\.NO NAME  |
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
00000100  7d 00 66 b8 b0 db 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

[CODE]

---

### Post by sikander3786 on 2010-11-25
The problem starts here

> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #2 for /boot/grub.

sda2 doesn't contain the relative files Grub is looking for.

Windows is still there. Boot files seem intact and you should be able to recover that by using the startup recovery (might need to be done 3 times) from a Windows installation/recovery disc. I'm saying that because I'm not sure if you'd be able to recover your Mint install or not as there seems to be some problem with partition table of Linux drives.

> sda4: __________________________________________________ _______________________

File system:
Boot sector type: -
Boot sector info:
Mounting failed:
mount: unknown filesystem type ''

sdb1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Unknown
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: 

You can try testdisk to recover those drives.

[https://help.ubuntu.com/community/DataRecovery#Testdisk](https://help.ubuntu.com/community/DataRecovery#Testdisk)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

And if recovered successfully you can just re-install Grub following the steps here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Wait for some other opinions as well ;-)

---

### Post by DeanG on 2010-11-26
The problem is that I have neither a Win7 recovery disk or an external drive to put it in. 

This netbook was to use f9 tor recovery  (I assume by accessing the Vista partition) but my boot sequence ends in grub> if I don't hit ESC and select a usb drive, so F9 is worthless.  I have tried unsuccessfully to find a link to a win7 recovery iso that I could put on a usb thumb drive

I have no data on this device and I would just like to get back to "Out of the Box State" so I can make another attempt at establishing a dual boot.  Next time I will pay more attention to the size of the partition that the Linux installer chooses automatically.

---

### Post by DeanG on 2010-11-26
I found a Win7 recovery here:[http://www.mediafire.com/?kdszp4wdvs3d2at]("http://www.mediafire.com/?kdszp4wdvs3d2at")

Download produced:
> CyberNetNews.com_Windows_7_32bit_Recovery_Disc.iso

When I booted to the usb thumb drive I got the following:

> SYSLINUX 3.86 2010-04-01 EBIOS Copywright 1994-2010 H. Peter Anvin et al
No DEFAULT or UI configuration directive found!
boot:_

---

### Post by sikander3786 on 2010-11-26
> **DeanG said:**
> I found a Win7 recovery here:[http://www.mediafire.com/?kdszp4wdvs3d2at]("http://www.mediafire.com/?kdszp4wdvs3d2at")

Download produced:


When I booted to the usb thumb drive I got the following:
Use the official Windows USB tool to create the starup USB not those that are intended for Linux.

[http://store.microsoft.com/help/iso-tool](http://store.microsoft.com/help/iso-tool)

---

### Post by DeanG on 2010-11-26
Sikander - I can't wait until your prediction comes true!

I'm running XP on my main windoz machine so I had to verify genuine windoz and install two prerequisites, one of which was an XP hotfix which probably broke all sorts of stuff.

[COLOR="Red"][SIZE="5"]AND THEN:[/SIZE][/COLOR]

```
The selected file is not a valid ISO file.  Please select a valid ISO file and try again.
```

Probably stuff you BUY from the Microsoft Store has a special flag.

This is how I got into this mess in the first place.  As you probably know, Win 7 starter is intentionally retarded and crippled so you you will send Microsoft another $80 to get a real (if you can call it that) copy of win7 home.

Anywhere else in the world, I could have bought this net-book from Azuz with Linux pre-installed but not in the US.  In fact I could not find a netbook by any manufacturer that was available in the US with Linux on it.  Since Linux is free I can only imagine that Microsoft is paying Asus and others to ship net-books with win 7 starter installed.

I could rail on this subject for hours but it is not going to solve my problem.  I going on a trip on Thursday and the main reason I bought this netbook was so that I wouldn't have to carry my old heavy (make that very heavy) laptop.

I'll continue to look for a repair iso and I do sincerely appreciate the assistance I receive here.

---

### Post by sikander3786 on 2010-11-26
What I would suggest now is to forget about your Linux install completely. Boot your recovery partition following the method below and restore your computer to the factory state. You need not the worry if you've backed up your important data.

See here on how to use Grub Rescue disc for booting Windows bootloaders.

[http://ubuntuforums.org/showthread.php?t=690912](http://ubuntuforums.org/showthread.php?t=690912)

Download the latest Super Grub Disc image here.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

And put it on USB using unetbooin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Other than that, you'll be doing everything as mentioned in that thread except that you will boot from the USB.

Hope it works this time.

---

### Post by DeanG on 2010-11-27
Step 5 resulted in the following - no success screen.

```
  Booting '1 hda1 sda1 (hd0,0) hd0s1 fat 7 GB WINDOWS'

set out_device=(hd0,0
set out_hurd+hd0
set out_hd=hd0
set out_linux_letter=a
set out_lide_hd=hda
set out_lscsi_hd=sda
set out_
set out_
set out_
set out_
set out_
set out_
set out_file=/boot/grub/state1
back
root (Hd0,0)
  Filesystem type is fat, partition type 0xb
setup (hd0)

Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/fat_stage1_5" exists... yes
Running "embed /boot/grub/fat_stage1_5 (hd0)"...
```


Appears to have failed!
Reboot ends in grub>

---

### Post by sikander3786 on 2010-11-27
I would request some senior members to take a look at your problem and advise.

Please hang in there.

---

### Post by Quackers on 2010-11-27
It may at some time be worthwhile to move the boot flag to sda1 and see if Windows will boot, OR see if F9 key opens the recovery partition. The F9 key (if that's the right key) must be tapped early in the boot sequence and until the recovery enmvironment is shown.

---

### Post by DeanG on 2010-11-27
I tried tapping F9 which I believe is the correct key based on the Product advertising but it did not change the result - still ended in grub>

I don't know how to change the "boot flag"

---

### Post by Quackers on 2010-11-27
It may be an idea to check which is the required key to boot from the recovery partition. Is there a manual for the machine?
If you boot to the Ubuntu Live usb and select "try ubuntu" and when the desktop loads go to System menu > Admin > Gparted you can move the boot flag by right-clicking on sda1 and choosing Manage Flags then check the Boot box and close.

---

### Post by DeanG on 2010-11-27
Can't locate manual perhaps this will help

[http://www.amazon.com/ASUS-1015PED-PU17-BK-10-1-Inch-Netbook-Black/dp/B003UNOVCC]("http://www.amazon.com/ASUS-1015PED-PU17-BK-10-1-Inch-Netbook-Black/dp/B003UNOVCC")

---

### Post by DeanG on 2010-11-27
TestDisk did the trick - I had it write a new MBR and windoz booted

Thanks to all for the help

---

