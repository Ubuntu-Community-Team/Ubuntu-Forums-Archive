---
title: "gnu grub version 1.97 beta4"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by abimiy on 2010-02-04
Iam abimiy and new here i need help,
 
 
Hi. I am using the latest version of Ubuntu Linux. I've been using it for about a month. One day, as i booted up my computer, something didn't go as planed. It started to boot up, but it went to some screen that said: "Gnu Grub version 1.97 beta 4 Minimal BASH-like editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device, file completions. Sh:grub> (it wants me to type something here)" How to i get rid of that screen. How to i get onto my Ubuntu Linux. HELP!

---

### Post by Herman on 2010-02-04
That usually means GRUB can't find the file called grub.cfg which is normally located inside your /boot/grub directory.

Normally the /boot/grub/grub.cfg file contains all the commands to tell GRUB how to present you with your GRUB Menu and the commands for booting whichever operating system you choose.

There are several alternative ways out of that situation, you can take your pick.

One way is to use GRUB's command line interface.
There are lots of things you may be able to do by typing your own GRUB commands.
Maybe you can get GRUB to look for the missing grub.cfg file by typing 'search -f /boot/grub/grub.cfg. If you can find it, issue the command something like: configfile (hd0,1)/boot/grub/grub.cfg and that should get your GRUB Menu back so you can boot as normal. (Replace the '(hd0,1)' part with whatever the answer was you got back from the search -f command).
After you boot, run 'sudo grub-mkconfig -o /boot/grub/grub.cfg to fix your GRUB.

Or, you can just boot with GRUB's command line interface. 
See this link for how to do that, [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html").

Another idea would be to boot your Ubuntu Live CD and chroot into your Ubuntu installation and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' to rebuild your lost grub.cfg file automatically.
For how to chroot see the following Ubuntu Web Forums thread: [how to chroot, simple and fast]("http://ubuntuforums.org/showthread.php?t=1156240"), by taavikko.

Yet another alternative would be to install another copy of Ubuntu in another partition beside the broken one and it should automatically install it's GRUB to MBR and detect the existing Ubuntu installation and add it to it's boot menu. 
It wouldn't matter if your second Ubuntu installation would be in a different hard disk or in a USB flash memory stick.
Then as soon as you boot your original Ubuntu, you just need to run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' to fix your grub in that if you want to.

I can probably think of a few more ideas of how you might go about getting back into your Ubuntu installation but that should be enough to get you started off with. :D

---

### Post by Herman on 2010-02-04
[LEFT]Probably that last idea, to install another Ubuntu, would be the easiest for you if you're new and not used to running commands.
[/LEFT]

---

### Post by zabo on 2010-02-07
When I type in 'search -f boot/grub/grub.cfg' the reply is 'loop0' and then I get just sh:grub> again...

How can I get back into Ubuntu?
Please help.

---

### Post by presence1960 on 2010-02-07
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by zabo on 2010-02-07
Thanks for the help! However, I have no Ubuntu on any USB. I'm using Wubi (I only have access to Windows now). Should I install Ubuntu on a USB to do get RESULTS.txt?

---

### Post by Herman on 2010-02-07
> When I type in 'search -f boot/grub/grub.cfg' the reply is 'loop0' and then I get just sh:grub> again... Try what salman4u did in the following thread, especially read post #10 there, [[ubuntu] I am really frustrated with this try hd0:NTFS]("http://ubuntuforums.org/showthread.php?t=1375035").
It is possible to boot your wubi installation using GRUB from the command line and then you can fix it.

I don't know very much about wubi, but I am inclined to agree with what presence1960 had to say in post#16 there too. I think (from what little I know), that wubi is only supposed to be a way to try Ubuntu out for a short time. If you want a real Ubuntu operating system I think you should consider installing it in a hard disk or in a USB in the normal way, (dual boot or something). 

Whatever you do have fun and enjoy Ubuntu. :D

---

### Post by hoboy on 2010-02-07
Guys check this link

[http://ubuntuforums.org/showthread.php?t=1314064&page=10](http://ubuntuforums.org/showthread.php?t=1314064&page=10)

---

### Post by amin5236 on 2010-02-19
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

...

 Paste the entire contents of that file back here. 
.

Hi, I did exactly what you said. Here is the result file pasted:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda7/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x075b075b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,199,154    51,199,092   7 HPFS/NTFS
/dev/sda2          51,199,155   312,560,639   261,361,485   f W95 Ext d (LBA)
/dev/sda5          51,199,218   138,319,649    87,120,432   7 HPFS/NTFS
/dev/sda6         138,319,713   225,440,144    87,120,432   7 HPFS/NTFS
/dev/sda7         225,440,208   312,560,639    87,120,432   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       e17341bc-1e25-4b88-b624-45016d756d0c   ext4                                     
/dev/sda1        16C0B683C0B6689F                       ntfs       (XP:C)                        
/dev/sda5        84C41D02C41CF7DE                       ntfs       (XP:Other)                    
/dev/sda6        BEF02AA2F02A613F                       ntfs       Videos&Sounds                 
/dev/sda7        D0586A4F586A33FE                       ntfs       Academic                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/(XP:C)            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
C:\wubildr.mbr = "Ubuntu"
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  68 62 69 6e 00 80 2f 00  00 10 00 00 00 00 00 00  |hbin../.........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 fe ff ff 76 00 32 00  2e 00 30 00 7c 00 41 00  |....v.2...0.|.A.|
00000030  63 00 74 00 69 00 6f 00  6e 00 3d 00 41 00 6c 00  |c.t.i.o.n.=.A.l.|
00000040  6c 00 6f 00 77 00 7c 00  41 00 63 00 74 00 69 00  |l.o.w.|.A.c.t.i.|
00000050  76 00 65 00 3d 00 46 00  41 00 4c 00 53 00 45 00  |v.e.=.F.A.L.S.E.|
00000060  7c 00 44 00 69 00 72 00  3d 00 49 00 6e 00 7c 00  ||.D.i.r.=.I.n.|.|
00000070  50 00 72 00 6f 00 74 00  6f 00 63 00 6f 00 6c 00  |P.r.o.t.o.c.o.l.|
00000080  3d 00 36 00 7c 00 50 00  72 00 6f 00 66 00 69 00  |=.6.|.P.r.o.f.i.|
00000090  6c 00 65 00 3d 00 50 00  72 00 69 00 76 00 61 00  |l.e.=.P.r.i.v.a.|
000000a0  74 00 65 00 7c 00 50 00  72 00 6f 00 66 00 69 00  |t.e.|.P.r.o.f.i.|
000000b0  6c 00 65 00 3d 00 50 00  75 00 62 00 6c 00 69 00  |l.e.=.P.u.b.l.i.|
000000c0  63 00 7c 00 52 00 41 00  34 00 3d 00 4c 00 6f 00  |c.|.R.A.4.=.L.o.|
000000d0  63 00 61 00 6c 00 53 00  75 00 62 00 6e 00 65 00  |c.a.l.S.u.b.n.e.|
000000e0  74 00 7c 00 52 00 41 00  36 00 3d 00 4c 00 6f 00  |t.|.R.A.6.=.L.o.|
000000f0  63 00 61 00 6c 00 53 00  75 00 62 00 6e 00 65 00  |c.a.l.S.u.b.n.e.|
00000100  74 00 7c 00 41 00 70 00  70 00 3d 00 25 00 53 00  |t.|.A.p.p.=.%.S.|
00000110  79 00 73 00 74 00 65 00  6d 00 52 00 6f 00 6f 00  |y.s.t.e.m.R.o.o.|
00000120  74 00 25 00 5c 00 73 00  79 00 73 00 74 00 65 00  |t.%.\.s.y.s.t.e.|
00000130  6d 00 33 00 32 00 5c 00  6e 00 65 00 74 00 70 00  |m.3.2.\.n.e.t.p.|
00000140  72 00 6f 00 6a 00 2e 00  65 00 78 00 65 00 7c 00  |r.o.j...e.x.e.|.|
00000150  4e 00 61 00 6d 00 65 00  3d 00 40 00 46 00 69 00  |N.a.m.e.=.@.F.i.|
00000160  72 00 65 00 77 00 61 00  6c 00 6c 00 41 00 50 00  |r.e.w.a.l.l.A.P.|
00000170  49 00 2e 00 64 00 6c 00  6c 00 2c 00 2d 00 33 00  |I...d.l.l.,.-.3.|
00000180  31 00 37 00 36 00 31 00  7c 00 44 00 65 00 73 00  |1.7.6.1.|.D.e.s.|
00000190  63 00 3d 00 40 00 46 00  69 00 72 00 65 00 77 00  |c.=.@.F.i.r.e.w.|
000001a0  61 00 6c 00 6c 00 41 00  50 00 49 00 2e 00 64 00  |a.l.l.A.P.I...d.|
000001b0  6c 00 6c 00 2c 00 2d 00  33 00 31 00 37 00 00 01  |l.l.,.-.3.1.7...|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 30 5a 31 05 00 00  |......?...0Z1...|
000001d0  c1 ff 05 fe ff ff 6f 5a  31 05 6f 5a 31 05 00 00  |......oZ1.oZ1...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Now what should I do?
Thanks in advance

---

### Post by presence1960 on 2010-02-19
> **amin5236 said:**
> Hi, I did exactly what you said. Here is the result file pasted:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda7/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x075b075b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,199,154    51,199,092   7 HPFS/NTFS
/dev/sda2          51,199,155   312,560,639   261,361,485   f W95 Ext d (LBA)
/dev/sda5          51,199,218   138,319,649    87,120,432   7 HPFS/NTFS
/dev/sda6         138,319,713   225,440,144    87,120,432   7 HPFS/NTFS
/dev/sda7         225,440,208   312,560,639    87,120,432   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       e17341bc-1e25-4b88-b624-45016d756d0c   ext4                                     
/dev/sda1        16C0B683C0B6689F                       ntfs       (XP:C)                        
/dev/sda5        84C41D02C41CF7DE                       ntfs       (XP:Other)                    
/dev/sda6        BEF02AA2F02A613F                       ntfs       Videos&Sounds                 
/dev/sda7        D0586A4F586A33FE                       ntfs       Academic                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/(XP:C)            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
C:\wubildr.mbr = "Ubuntu"
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  68 62 69 6e 00 80 2f 00  00 10 00 00 00 00 00 00  |hbin../.........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 fe ff ff 76 00 32 00  2e 00 30 00 7c 00 41 00  |....v.2...0.|.A.|
00000030  63 00 74 00 69 00 6f 00  6e 00 3d 00 41 00 6c 00  |c.t.i.o.n.=.A.l.|
00000040  6c 00 6f 00 77 00 7c 00  41 00 63 00 74 00 69 00  |l.o.w.|.A.c.t.i.|
00000050  76 00 65 00 3d 00 46 00  41 00 4c 00 53 00 45 00  |v.e.=.F.A.L.S.E.|
00000060  7c 00 44 00 69 00 72 00  3d 00 49 00 6e 00 7c 00  ||.D.i.r.=.I.n.|.|
00000070  50 00 72 00 6f 00 74 00  6f 00 63 00 6f 00 6c 00  |P.r.o.t.o.c.o.l.|
00000080  3d 00 36 00 7c 00 50 00  72 00 6f 00 66 00 69 00  |=.6.|.P.r.o.f.i.|
00000090  6c 00 65 00 3d 00 50 00  72 00 69 00 76 00 61 00  |l.e.=.P.r.i.v.a.|
000000a0  74 00 65 00 7c 00 50 00  72 00 6f 00 66 00 69 00  |t.e.|.P.r.o.f.i.|
000000b0  6c 00 65 00 3d 00 50 00  75 00 62 00 6c 00 69 00  |l.e.=.P.u.b.l.i.|
000000c0  63 00 7c 00 52 00 41 00  34 00 3d 00 4c 00 6f 00  |c.|.R.A.4.=.L.o.|
000000d0  63 00 61 00 6c 00 53 00  75 00 62 00 6e 00 65 00  |c.a.l.S.u.b.n.e.|
000000e0  74 00 7c 00 52 00 41 00  36 00 3d 00 4c 00 6f 00  |t.|.R.A.6.=.L.o.|
000000f0  63 00 61 00 6c 00 53 00  75 00 62 00 6e 00 65 00  |c.a.l.S.u.b.n.e.|
00000100  74 00 7c 00 41 00 70 00  70 00 3d 00 25 00 53 00  |t.|.A.p.p.=.%.S.|
00000110  79 00 73 00 74 00 65 00  6d 00 52 00 6f 00 6f 00  |y.s.t.e.m.R.o.o.|
00000120  74 00 25 00 5c 00 73 00  79 00 73 00 74 00 65 00  |t.%.\.s.y.s.t.e.|
00000130  6d 00 33 00 32 00 5c 00  6e 00 65 00 74 00 70 00  |m.3.2.\.n.e.t.p.|
00000140  72 00 6f 00 6a 00 2e 00  65 00 78 00 65 00 7c 00  |r.o.j...e.x.e.|.|
00000150  4e 00 61 00 6d 00 65 00  3d 00 40 00 46 00 69 00  |N.a.m.e.=.@.F.i.|
00000160  72 00 65 00 77 00 61 00  6c 00 6c 00 41 00 50 00  |r.e.w.a.l.l.A.P.|
00000170  49 00 2e 00 64 00 6c 00  6c 00 2c 00 2d 00 33 00  |I...d.l.l.,.-.3.|
00000180  31 00 37 00 36 00 31 00  7c 00 44 00 65 00 73 00  |1.7.6.1.|.D.e.s.|
00000190  63 00 3d 00 40 00 46 00  69 00 72 00 65 00 77 00  |c.=.@.F.i.r.e.w.|
000001a0  61 00 6c 00 6c 00 41 00  50 00 49 00 2e 00 64 00  |a.l.l.A.P.I...d.|
000001b0  6c 00 6c 00 2c 00 2d 00  33 00 31 00 37 00 00 01  |l.l.,.-.3.1.7...|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 30 5a 31 05 00 00  |......?...0Z1...|
000001d0  c1 ff 05 fe ff ff 6f 5a  31 05 6f 5a 31 05 00 00  |......oZ1.oZ1...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Now what should I do?
Thanks in advance
Unfortunately you installed via wubi. I know close to nothing about wubi. maybe you should wait until someone knowledgeable in wubi comes along. sorry I can't be of any help.

---

### Post by meierfra. on 2010-02-20
You have been hit by a bug in Grub 2 ntfs module. For all the details and the easy fix see:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by IchBinWamphyri on 2010-04-06
[B][SIZE=2]just got my girlfriends laptop working, hope this helps you too.[/SIZE]
 []("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")[/B]

 **[Solution]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")**

   **Warning:  The solution below is only for Wubi 9.10. It will make older versions unbootable.** 
  Boot into Windows and click on the following link to download the file "wubildr": 
  [wubildr]("http://launchpadlibrarian.net/36920146/wubildr") 
  Don't try to open the file. Move the file to "C:\" to replace the faulty "C:\wubildr". (to get to "C:\" go to "My Computer" or "Computer" and double click the "C:drive") 
  If Wubi is not on the C:drive, you might need to place wubildr into the partition containing Wubi. So if Wubi is not on the C:\drive, repeat the above instructions, using the drive letter of the partition containing Wubi in place of "C:".

---

### Post by Thunder72 on 2011-05-11
Hi Hermen,

I followed your instruction and I used chroot to reconfigure the grub.cfg and its detected the kernels that installed. after that I exited from bash and restart it but still the grub doesn't know my hard disk i.e. in /dev i can not find any sdx 

is there any solution for that

PS: I have only linux on it there is no windows or wubi

---

### Post by drs305 on 2011-05-11
> **Thunder72 said:**
> Hi Hermen,

I followed your instruction and I used chroot to reconfigure the grub.cfg and its detected the kernels that installed. after that I exited from bash and restart it but still the grub doesn't know my hard disk i.e. in /dev i can not find any sdx 

is there any solution for that

PS: I have only linux on it there is no windows or wubi

Thunder72,

Welcome to the Ubuntu forums. For us to see the status of your boot files, please download and run the boot info script from the LiveCD. The script will generate a file called RESULTS.txt. Please post the contents of RESULTS.txt.

The boot info script link is in my signature line (BIS).

---

### Post by Thunder72 on 2011-05-12
Dear drs305

please find the requested file
[PHP]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders, total 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,098,239    40,098,177  83 Linux
/dev/sda2          40,098,240    41,929,649     1,831,410   5 Extended
/dev/sda5          40,098,303    41,929,649     1,831,347  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e3201d3d-8645-43cf-8ee6-27988b9498c8   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8c00e9d2-645f-4eb4-a26f-b86745f4d744   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root e3201d3d-8645-43cf-8ee6-27988b9498c8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e3201d3d-8645-43cf-8ee6-27988b9498c8
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e3201d3d-8645-43cf-8ee6-27988b9498c8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e3201d3d-8645-43cf-8ee6-27988b9498c8
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e3201d3d-8645-43cf-8ee6-27988b9498c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e3201d3d-8645-43cf-8ee6-27988b9498c8
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e3201d3d-8645-43cf-8ee6-27988b9498c8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e3201d3d-8645-43cf-8ee6-27988b9498c8
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e3201d3d-8645-43cf-8ee6-27988b9498c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e3201d3d-8645-43cf-8ee6-27988b9498c8
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=e3201d3d-8645-43cf-8ee6-27988b9498c8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e3201d3d-8645-43cf-8ee6-27988b9498c8
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=e3201d3d-8645-43cf-8ee6-27988b9498c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e3201d3d-8645-43cf-8ee6-27988b9498c8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e3201d3d-8645-43cf-8ee6-27988b9498c8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e3201d3d-8645-43cf-8ee6-27988b9498c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8c00e9d2-645f-4eb4-a26f-b86745f4d744 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   1.9GB: boot/grub/core.img
    .5GB: boot/grub/grub.cfg
   7.8GB: boot/initrd.img-2.6.32-31-generic
   8.3GB: boot/initrd.img-2.6.35-28-generic
   8.6GB: boot/initrd.img-2.6.38-8-generic
   4.3GB: boot/vmlinuz-2.6.32-31-generic
   7.2GB: boot/vmlinuz-2.6.35-28-generic
   9.7GB: boot/vmlinuz-2.6.38-8-generic
   8.6GB: initrd.img
   8.3GB: initrd.img.old
   9.7GB: vmlinuz
   7.2GB: vmlinuz.old

[/PHP]

---

### Post by drs305 on 2011-05-12
> **Thunder72 said:**
> ... it but still the grub doesn't know my hard disk i.e. in /dev i can not find any sdx 


Thanks for posting the RESULTS.txt.

Your files look correct. Before we purge/reinstall grub, please at the grub prompt run these commands and let us know what you get:

```
ls  # Should show (hd0), (hd0,1), (hd0,5)
ls (hd0,1)/boot  # Should show *vmlinuz* and *initrd.img*
ls (hd0,1)/boot/grub # Should show a lot of *.mod files.
ls (hd0,1)/boot/grub/grub.cfg # Should return "grub.cfg"

```

I notice this is a *very* small hard drive. How old is the computer? If it is very old, please during boot access the BIOS setup and see what size of hard disk your BIOS reports.

---

### Post by Thunder72 on 2011-05-12
I can see grub.cfg as I mentioned previously but I cannot see any hard disk inside dev folder

when I boot from live cd and reinstall the grub it was installed successfully but when I reboot is has the same issue

I am using vm to test before deploy on my life environment

---

### Post by drs305 on 2011-05-12
> **Thunder72 said:**
> I can see grub.cfg as I mentioned previously but I cannot see any hard disk inside dev folder

when I boot from live cd and reinstall the grub it was installed successfully but when I reboot is has the same issue

I am using vm to test before deploy on my life environment

What we need to know is what GRUB sees at the grub prompt. Once an OS is booted the OS can look for files, but what the OS sees can be different than what Grub can see. It may be just the terms we are using, but to me '/dev' means you are looking from within an operating system (since grub2 doesn't lists things as 'hd...' Your system may have a big problem in not seeing drives in /dev, but we need to determine if the problem is with Grub or if it occurs later within the OS.

Also, since you mention a vm, are your issues within the VM or a normal OS (I've been assuming the normal OS).

---

### Post by Thunder72 on 2011-05-15
Dear drs305

sorry for latency, yes grub can see grub.cfg

I am trying to follow this steps
1)grub> linux  (hd0,1)/vmlinuz root=/dev/sda1
2)grub> initrd  (hd0,1)/initrd.img
3)grub> boot


the first one I have to type root=/dev/sda1 which I mentioned that my device doesn't see any sd or hd in /dev

---

### Post by drs305 on 2011-05-15
> **Thunder72 said:**
> Dear drs305

sorry for latency, yes grub can see grub.cfg

I am trying to follow this steps
1)grub> linux  (hd0,1)/vmlinuz root=/dev/sda1
2)grub> initrd  (hd0,1)/initrd.img
3)grub> boot


the first one I have to type root=/dev/sda1 which I mentioned that my device doesn't see any sd or hd in /dev

When you say "in /dev" are you at the grub prompt during boot? And if you type "ls" do you not get "(hd0) (hd0,1)" ?

---

### Post by Thunder72 on 2011-05-15
i have only grub prompt and when i type ls i got
(hd0) (hd0,1) (hd0,5)...
and when i type ls (hd0,1)/boot/grub/
i got grub.cfg
and if i typed ls (hd0,1)/dev/
i can not see any sd or hd only ram and tty and the other devices

hope this help

---

### Post by drs305 on 2011-05-15
Thunder72,

You hard drive is very small. I suspect your BIOS might only be able to see the first 8GB of your drive. 

Reboot, enter BIOS and check the reported drive size. See if it says your drive is only 8GB.

Continue to the grub prompt, then try this:
```
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod normal
normal

```

Note, in the following, you can use the UP/DN keys to recall a previous command and edit it.
If that doesn't boot, continue with this:
```
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

```
If that doesn't boot, continue with:
```
linux (hd0,1)/boot/vmlinuz-2.6.38-8-generic root=/dev/sda1 ro
initrd (hd0,1)/boot/initrd.img-2.6.38-8-generic
boot

```

If that doesn't boot, continue with:
```
linux (hd0,1)/boot/vmlinuz-2.6.35-28-generic root=/dev/sda1 ro
initrd (hd0,1)/boot/initrd.img-2.6.35-28-generic
boot
```

---

### Post by Thunder72 on 2011-05-15
thank for your help, it's working now
my mistake that when i typed the command
linux (hd0,1)/boot/grub root=/dev/sda1 ro
when i reach typing dev i normally use tab to continue my command which is not show the sda1 
now i understand that this command basically map the (hd0,1) to sda1

thanks again i appreciate your help :)

---

