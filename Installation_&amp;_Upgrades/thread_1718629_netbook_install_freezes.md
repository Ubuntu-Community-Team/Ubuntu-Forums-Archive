---
title: "netbook install freezes"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by relmoyd on 2011-03-31
I am trying to install Ubuntu 10.10 on my HP 110 netbook using the USB stick drive procedure and it freezes at the "Preparing to Install" screen.  Please suggest something.

---

### Post by Hedgehog1 on 2011-03-31
[FONT=Times New Roman][SIZE=2]We need see the current layout of your disk partitions.[/SIZE][/FONT]
[SIZE=2] [/SIZE]
[FONT=Times New Roman][SIZE=2]Please boot off the LiveCD/LiveUSB, select 'TRY', and then:[/SIZE][/FONT]
[SIZE=2] [/SIZE]
[FONT=Times New Roman][SIZE=2][http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]Follow the instruction on the website and post the results here.[/SIZE][/FONT]
[SIZE=2] [/SIZE]
[SIZE=2] [/SIZE]
[FONT=Times New Roman][SIZE=2]***The Hedge***[/SIZE][/FONT]
[SIZE=2] [/SIZE]
[FONT=Times New Roman][SIZE=2]:KS[/SIZE][/FONT]

---

### Post by relmoyd on 2011-03-31
[FONT=Courier New][SIZE=1]The netbook is new; I have not started it with Windows.  Thanks.

Here is the content of RESULTS.txt:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   450,230,271   449,820,672   7 HPFS/NTFS
/dev/sda3         450,230,272   488,183,807    37,953,536   7 HPFS/NTFS
/dev/sda4         488,183,808   488,395,119       211,312   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3926 MB, 3926949888 bytes
16 heads, 16 sectors/track, 29960 cylinders, total 7669824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,669,823     7,661,760   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9484C85884C83E8C                       ntfs       SYSTEM                        
/dev/sda2        928862C58862A785                       ntfs                                     
/dev/sda3        86FED17DFED16649                       ntfs       RECOVERY                      
/dev/sda4        B66E-F484                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        15F5-3967                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  c0 e8 74 00 3b 3a 00 00  00 00 00 00 02 00 00 00  |..t.;:..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 67 39 f5 15 4e  4f 20 4e 41 4d 45 20 20  |..)g9..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 9a  74 00 00 66 ba 00 00 00  |..E}.f..t..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


[/SIZE][/FONT]

---

### Post by Hedgehog1 on 2011-03-31
Well, I can tell you why the Ubuntu install freezes.

You are allowed only 4 primary partitions on a disk.

Your disk already has all 4 in place:

[B]/dev/sda1 9484C85884C83E8C ntfs SYSTEM 
/dev/sda2 928862C58862A785 ntfs 
/dev/sda3 86FED17DFED16649 ntfs RECOVERY 
/dev/sda4 B66E-F484 vfat HP_TOOLS[/B] 

In this situation, I typically ask folks to _make 2 sets of recovery DVDs as well as a Windows rescue CD (and save these in a safe place)_.

Then I have them delete the 'RECOVERY' partition (the DVDs will serve that purpose now) and we install Ubuntu there.

I have a full example of this with pictures.  I will post the example below.

***The Hedge***

:KS

**p.s. If your desire is an Ubuntu ONLY install, please let me know as the install is a little different**

---

### Post by Hedgehog1 on 2011-03-31
When all four primary partitions are taken (the HP install)

[SIZE="4"][COLOR="DarkOrange"]First how it looks in Windows:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]What it looks like in gparted off the LiveCD:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right click on sda3 and select 'Delete':[/COLOR][/SIZE]
[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the 'check' mark button to really make the change:[/COLOR][/SIZE]
[IMG]http://img190.imageshack.us/img190/1732/hp4partitions04.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right Click, on empty area, select new and create extended sda3 (Press that check mark button again...):[/COLOR][/SIZE]
[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create you sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-03-31
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Select this during the install:[/COLOR][/SIZE]
[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]And you will get to here:[/COLOR][/SIZE]
[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]We will add some extra data to sda5 and sda6.  With sda5 highlighted, press the [CHANGE] button:[/COLOR][/SIZE]
[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]These settings prepare the partition to be exdt4, '/'.[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkOrange"]Repeat the steps for the swap area (This usually set itself up OK) :[/COLOR][/SIZE]
[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]You are ready to install.  Press [Install Now].[/COLOR][/SIZE]
[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG] 

***The Hedge***

:KS

---

### Post by relmoyd on 2011-04-01
I would like an Ubuntu only install.  If possible, I would like to preserve the RECOVERY partition.

Also, gparted crashes.

---

### Post by Hedgehog1 on 2011-04-01
Your gonna make this hard on me, huh?

OK - We can deal with this.

The first 2 partitions are Windows 7, the last 2 are the HP recovery and tools.

We will leave BOTH the recovery and tools on the disk, so you can reinstall windows later if you wish.

> Also, gparted crashes.

There is a bug that on some brands of USB sticks gparted fails when started on 10.10 LiveUSB.  10.04 works just fine on those same USB sticks.

Would you prefer a 10.04 LTS (**L**ong **T**erm **S**upport) install?  If so, you can create the LiveUSB with 10.04 and gparted will function.

If you want 10.10, please load a different brand of USB stick with 10.10.

Either way, you will use gparted and delete /dev/sda1 & /dev/sda2.

Then, you will create the partitions again, this time for Ubuntu:

**/dev/sda1** *ext4* '/' all the available space excepted for what swap needs.
**/dev/sda2** *swap* make this the same size of your RAM plus 10%

Then you can use the pictures I already posted, and everywhere it says /dev/sda**5**, you do /dev/sda**1**.  Everywhere it says /dev/sda**6**, you do /dev/sda**2**.  *You can skip the extended partition step - you will not need it at this time.*

Please choose on 10.10 on a different USB, or 10.04LTS on your current USB.  Then you are ready to go!



***The Hedge***

:KS

p.s. I would encourage you to make the recovery DVDs and Windows rescue CD in case you want to go back to windows, but the choice is yours...

---

### Post by relmoyd on 2011-04-01
Where can I find the iso for 10.04 LTS netbook edition?  (The website is not helpful with this.)

---

### Post by Dutch70 on 2011-04-01
> **relmoyd said:**
> Where can I find the iso for 10.04 LTS netbook edition?  (The website is not helpful with this.)

[[COLOR="Red"]http://www.ubuntu.com/netbook/get-ubuntu/download[/COLOR]]("http://www.ubuntu.com/netbook/get-ubuntu/download")

---

### Post by relmoyd on 2011-04-01
This link has the 10.10 netbook installation ISO.  I need the 10.04 LTS netbook ISO.

---

### Post by Hedgehog1 on 2011-04-01
Here is the page for 10.04.02 LTS downloads:

[http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")

You want the '**ubuntu-10.04-netbook-i386.iso**' version.



***The Hedge***

:KS

---

### Post by relmoyd on 2011-04-02
On boot, ubuntu-10.04-netbook-i386.iso hangs here:
SYSLINUX 3.86 2010-04-01 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al

---

### Post by Dutch70 on 2011-04-02
What did you use to create the usb stick? 

[[COLOR="Red"]Unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/") is a really good one.

---

### Post by relmoyd on 2011-04-02
i have purchase a Patriot USB flash drive and installed 10.10 netbook remix install image on it using the USB installer software from [www.pendrivelinux.com](www.pendrivelinux.com).  The gparted operations appear to work correctly.  I have modified my partions so that I have a 210 GB ext4 partition labeled Ubuntu at /dev/sda1 and a 3 GB linux-swap drive at /dev/sda2 and the installation appears to be progressing.  It is now at the "Allocate drive space" screen.

---

### Post by Hedgehog1 on 2011-04-02
Great news!

Hope to read you are posting from your Ubuntu install soon!

Hardware can just drive you nuts some days, can't it?

***The Hedge***

:KS

---

