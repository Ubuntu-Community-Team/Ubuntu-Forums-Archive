---
title: "After Win install, NO ubuntus I try will install."
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by cacycleworks on 2010-11-04
Hey All,

I've been an ubuntu fan since 7.4 or so ... never had a situation quite like this. Install problems before had always been quite consistent. I'm re-furbing a PC ... is almost an entirely new build using a new Gagabyte GA-EP43T-USB3 motherboard. (Intel's P43 chipset)

When initially starting the build, I installed ubuntu 10.10 via USB and left a ntfs partition knowing that I was going to be following up with a winxp install. So far so good ... booted into ubuntu a handful of times then eventually got windows working.

Now, it's time to fire up the "live CD" usb stick to get my grub back. No go. It stops before ANYthing with a screen full of normal log gibberish and:
[FONT="Courier New"][12.0002342] Stack:[/FONT]

Ok, cool. So I try another stick that has slitaz on it. Instant boot (as usual) and right to the desktop, no problem. Soooo, on to other ubuntus I have laying about (all of these failed at some point of the install):

» ubuntu 10.10 64bit ALT CD: hangs after trying to detect pcmcia cards
» ubuntu 10.04 64bit server CD: hangs during ncurses menus after configuring network
» kubuntu 9.10 ALT amd64 Desktop CD: hangs during ncurses menus before configuring network
» ubuntu 10.10 64bit ALT usb: hangs with hardware probing and leaves the caps and num lock LEDs flashing on the PS2 keyboard.

But my IT chainsaws work awesome:
» Slitaz booting from usb (debian like linux)
» Knoppix 5.1 booting from CD

Any suggestions for tomorrow when I start randomly entering boot strings disabling things?? And I keep PS2 keyboards around because they will always let you enter setup or boot menus. :)

Thanks in advance,
Chris

---

### Post by cacycleworks on 2010-11-06
seriously? no thoughts? :confused:

I was hoping this computer would get to have ubuntu...

---

### Post by Rubi1200 on 2010-11-06
It would help us greatly if you could boot with a LiveCD and post the results of the boot-script linked at the bottom of my post.

Having a better overview of your setup will make offering solutions easier.

Thanks.

---

### Post by cacycleworks on 2010-11-06
Thanks -- will do that at work tomorrow or monday. :)

---

### Post by cacycleworks on 2010-11-08
> **Rubi1200 said:**
> It would help us greatly if you could boot with a LiveCD and post the results of the boot-script linked at the bottom of my post.

Not much to report... it all makes sense. hda2 & 3 are unformatted partitions (planning on putting win7 there). hda6&7 are ext4. Fat32 space at end is where I'll put images from a disc imaging tool I use.

[SIZE="1"]```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/hda

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

hda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

hda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

hda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


hda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hda7,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


hda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdc: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hda1    *          2,048   152,381,439   152,379,392   7 HPFS/NTFS
/dev/hda2         152,392,590   250,035,659    97,643,070  83 Linux
/dev/hda3         250,035,660   269,570,699    19,535,040  83 Linux
/dev/hda4         269,570,700   488,392,064   218,821,365   5 Extended
/dev/hda5         269,570,763   277,378,289     7,807,527  82 Linux swap / Solaris
/dev/hda6         277,378,353   345,734,864    68,356,512  83 Linux
/dev/hda7         345,734,928   414,091,439    68,356,512  83 Linux
/dev/hda8         414,091,503   488,392,064    74,300,562   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/cloop0                                             iso9660    KNOPPIX_FS                    
/dev/hda1                                               ntfs                                     
/dev/hda5                                               swap                                     
/dev/hda6        aa95eb3f-cb61-4894-81b4-c8355a157b3f   ext3                                     
/dev/hda7        24d40697-19b0-40fa-8c66-014c857d8724   ext3                                     
/dev/hda8        183E-A203                              vfat                                     
/dev/hdc                                                iso9660    KNOPPIX                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/root        /                        ext2       (rw)
/dev/hdc         /cdrom                   iso9660    (ro)
/dev/cloop       /KNOPPIX                 iso9660    (ro)
/dev/pts         /dev/pts                 devpts     (rw)


================================ hda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on hda2

00000000  92 97 74 06 a3 0a b0 00  82 80 05 05 ac ee 66 59  |..t...........fY|
00000010  5e fc a4 02 0a 8a 00 75  05 0b fc 4c 4d f2 ee 94  |^......u...LM...|
00000020  a4 8d 67 81 cb 79 a3 f2  61 a9 93 de 52 00 a5 87  |..g..y..a...R...|
00000030  3c e8 80 28 79 fc 91 6b  a9 51 f8 f0 01 1c 05 b2  |<..(y..k.Q......|
00000040  2a d9 4c 02 87 8d 00 26  43 cb 0d e3 66 e3 4f 40  |*.L....&C...f.O@|
00000050  92 97 75 06 f6 6e a7 f2  71 fe 66 df 4f bd c7 ab  |..u..n..q.f.O...|
00000060  ac 8b c8 2f 5b fa 3b f9  0b b9 00 6d 07 39 02 95  |.../[.;....m.9..|
00000070  eb af e8 7f a6 fe 35 41  d6 c9 f7 0b ac 50 35 2f  |......5A.....P5/|
00000080  e5 ff e3 af e3 98 f6 f3  1b b2 84 86 37 0b ff 91  |............7...|
00000090  b7 3f 95 3f 96 bf f2 38  cc c6 67 ca fc a0 7b 3a  |.?.?...8..g...{:|
000000a0  92 97 76 06 b6 04 3c d3  a8 5c f2 01 1f 95 2e 65  |..v...<..\.....e|
000000b0  d3 8a b6 8d 72 57 55 4c  41 5c 2a 3c 26 8c 01 f4  |....rWULA\*<&...|
000000c0  b7 02 a1 1c 84 38 0a 15  08 3c 7f 09 98 5a b8 80  |.....8...<...Z..|
000000d0  41 24 10 f5 55 a4 1f c8  96 24 a0 e1 ff 9d 26 00  |A$..U....$....&.|
000000e0  68 7b 55 37 00 94 03 a6  a6 00 08 a7 1d 2d 7a 91  |h{U7.........-z.|
000000f0  92 97 77 06 ad 94 44 18  1d 85 81 46 b2 ea 52 b8  |..w...D....F..R.|
00000100  1e 85 ad 05 15 50 f2 09  08 7c 4f c9 86 a3 4d be  |.....P...|O...M.|
00000110  ad 00 b5 10 1d aa e2 f7  70 3f 20 1a b2 af ad 02  |........p? .....|
00000120  f0 f0 fa 55 03 89 1e 2f  80 cf ff 18 00 1a 1b df  |...U.../........|
00000130  e7 cc 18 9a 2c 95 01 a6  21 ce 78 a5 fa 0f 60 00  |....,...!.x...`.|
00000140  72 97 08 ff ff ff ff ff  00 00 00 00 00 00 00 00  |r...............|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000190  92 97 78 08 3f af e3 7f  7b 2c e7 cc b9 4c e6 50  |..x.?...{,...L.P|
000001a0  3a 10 4b 2d cf e3 6f 6e  4a 63 7e 6e 95 89 49 e8  |:.K-..onJc~n..I.|
000001b0  5c ae af bf d9 da 5e ce  c2 59 b3 76 70 89 76 2e  |\.....^..Y.vp.v.|
000001c0  bf bb d9 ee c7 5f 77 3c  6d 2e 70 c4 f8 b8 e0 67  |....._w<m.p....g|
000001d0  92 4e 2d 36 90 0b 05 34  c2 d7 d8 30 f8 f4 33 c8  |.N-6...4...0..3.|
000001e0  92 97 79 08 a2 87 d0 13  48 3c 9a 6b 75 05 ef c0  |..y.....H<.ku...|
000001f0  47 8e a2 87 53 4a 97 9a  03 83 8d 18 43 b1 8d 16  |G...SJ......C...|
00000200

Unknown BootLoader  on hda3

00000000  b5 93 46 f5 a2 c5 1c 0c  db 39 03 00 e7 a7 e1 53  |..F......9.....S|
00000010  68 37 a8 2f 84 5b dc 2b  e4 0d 9e b9 ad 6e 91 8b  |h7./.[.+.....n..|
00000020  d4 a5 2e a0 9e 4d f1 7d  92 b5 ac e7 70 cf cc 57  |.....M.}....p..W|
00000030  3d bd 71 5a 7a 5e b3 34  12 b4 36 f2 0b 94 23 3f  |=.qZz^.4..6...#?|
00000040  67 9c 6e 05 71 92 0f 7e  9d fd aa ae 4c b5 3f ff  |g.n.q..~....L.?.|
00000050  d7 f5 2d 41 22 ff 00 8f  ab 09 e7 45 98 73 03 b6  |..-A"......E.s..|
00000060  76 9e ff 00 4a 5d 3b 56  bb d2 af 6d 3c 8e bb 4a  |v...J];V...m<..J|
00000070  36 79 07 3e b5 d6 c2 5a  9d 48 8c 6a 72 2c d2 6d  |6y.>...Z.H.jr,.m|
00000080  04 8c 0f 45 ad 95 d1 60  b9 d3 d6 d6 27 54 9c 1d  |...E...`....'T..|
00000090  e8 e5 be f1 f4 35 2c 9b  9c cc eb 71 6e c6 1b 98  |.....5,....qn...|
000000a0  9a 39 03 61 95 bb 54 ca  c2 15 2b 92 c7 19 e3 9a  |.9.a..T...+.....|
000000b0  13 56 29 ab 33 a1 d3 66  57 11 c3 9e 64 70 bb 94  |.V).3..fW...dp..|
000000c0  e7 02 a4 bf b1 6b 59 48  0e 64 88 b7 05 78 3f 8d  |.....kYH.d...x?.|
000000d0  44 c1 1f ff d0 fa 40 6f  1c 05 3f 43 d6 94 64 e4  |D.....@o..?C..d.|
000000e0  9c 8f c6 98 d5 c2 28 c4  41 54 16 6f 72 d9 26 9e  |......(.AT.or.&.|
000000f0  3a 00 09 e3 a9 3c 9a 96  57 51 54 02 47 73 e9 49  |:....<..WQT.Gs.I|
00000100  b4 aa f0 49 c7 7e a4 d2  10 bb 1b a7 0f f4 ed 48  |...I.~.........H|
00000110  03 73 f2 9e 0e 3a e7 f1  a2 fa 8e c7 ff d1 fa 50  |.s...:.........P|
00000120  c8 41 2c df c3 ea 28 2c  a4 6d 65 5e 4e 79 a2 da  |.A,...(,.me^Ny..|
00000130  97 7b 06 57 1d 31 f4 a3  e7 ca e1 ca ff 00 c0 a9  |.{.W.1..........|
00000140  df 51 5f 51 a6 47 23 0e  bb b3 d3 7a 86 fe 75 0c  |.Q_Q.G#....z..u.|
00000150  96 da 74 ac 4c fa 6d a3  31 39 cf 97 8f e5 f5 a5  |..t.L.m.19......|
00000160  60 bb d8 ad fd 87 a1 39  f3 16 da 58 46 49 06 09  |`......9...XFI..|
00000170  dd 0e 7d 71 9f 5a 74 5a  4c 30 7c b0 eb 3a 9e dc  |..}q.ZtZL0|..:..|
00000180  f0 92 4d bc 63 f1 ff 00  3c 52 6d b0 ba ec 7f ff  |..M.c...<Rm.....|
00000190  d2 fa 44 40 d1 80 52 54  63 9c 9c 8c d2 e5 97 e6  |..D@..RTc.......|
000001a0  78 58 a9 38 dc 84 0c 1f  a5 27 b1 60 1a 17 1b 86  |xX.8.....'.`....|
000001b0  e0 78 e8 2a 4c 2e 02 8c  e4 f4 a0 04 50 c3 6e 00  |.x.*L.......P.n.|
000001c0  19 e3 1d f3 4d ee 48 60  46 70 79 c9 14 00 a0 74  |....M.H`Fpy....t|
000001d0  2d 90 3a 9c 8e d4 80 a9  51 92 01 f5 23 f5 a6 23  |-.:.....Q...#..#|
000001e0  ff d3 fa 53 00 63 e7 39  53 f8 52 1d d9 ca 92 79  |...S.c.9S.R....y|
000001f0  fe ef 26 a9 6a 86 20 0e  d9 e0 63 1c fb d2 84 25  |..&.j. ...c....%|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

No RAID disks 
=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file

```[/SIZE]

---

### Post by cacycleworks on 2010-11-08
Symptoms: ubuntu 10.10 installed ok. Installed XP (still works) and then nothing I do to reinstall, usb, or liveCD ubuntu works. Slitaz boots usb, Knoppix boots CD (on it now)

Through XP, I installed a lot of drivers and crap for the motherboard and I'm wondering if that's the real problem. :(

This system's current configuration:
MoBoard: Gigabyte GA-EP43T-USB3 (intel p43 chipset, no onboard video)
CPU: Pentium 4 630. (core 2 duo replacement is on its way)
RAM: 2x 2GB AData xtreme ddr3 2000
Video: evga 210 nvidia geForce 512MB
HD: sata2 250G. Seems fine.
has CD/DVD/r combo drive, works fine

This system is somewhat overclocked and water cooled and cpu rarely gets above ambient temp. This cpu is supposed to be 64bit capable (has lm - long mode) flag in /proc/cpu ... however, the ubuntu cd's should at least boot up and tell me wrong architecture if this was a 32/64 bit problem.

(lspci-v output attached)

---

### Post by cacycleworks on 2010-11-08
For the bored:
```
# cat cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 3
cpu MHz         : 3733.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 8709.37

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 3
cpu MHz         : 3733.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 8702.72

```

---

### Post by cybergnome on 2010-11-08
> **cacycleworks said:**
> Hey All,

I've been an ubuntu fan since 7.4 or so ... never had a situation quite like this. Install problems before had always been quite consistent. I'm re-furbing a PC ... is almost an entirely new build using a new Gagabyte GA-EP43T-USB3 motherboard. (Intel's P43 chipset)

When initially starting the build, I installed ubuntu 10.10 via USB and left a ntfs partition knowing that I was going to be following up with a winxp install. So far so good ... booted into ubuntu a handful of times then eventually got windows working.

Now, it's time to fire up the "live CD" usb stick to get my grub back. No go. It stops before ANYthing with a screen full of normal log gibberish and:
[FONT=Courier New][12.0002342] Stack:[/FONT]

Ok, cool. So I try another stick that has slitaz on it. Instant boot (as usual) and right to the desktop, no problem. Soooo, on to other ubuntus I have laying about (all of these failed at some point of the install):

» ubuntu 10.10 64bit ALT CD: hangs after trying to detect pcmcia cards
» ubuntu 10.04 64bit server CD: hangs during ncurses menus after configuring network
» kubuntu 9.10 ALT amd64 Desktop CD: hangs during ncurses menus before configuring network
» ubuntu 10.10 64bit ALT usb: hangs with hardware probing and leaves the caps and num lock LEDs flashing on the PS2 keyboard.

But my IT chainsaws work awesome:
» Slitaz booting from usb (debian like linux)
» Knoppix 5.1 booting from CD

Any suggestions for tomorrow when I start randomly entering boot strings disabling things?? And I keep PS2 keyboards around because they will always let you enter setup or boot menus. :)

Thanks in advance,
Chris


The windows installation CD by default uses the entire disk and overwrites the MBR.  If grub was installed to the MBR, it's gone, and you won't be able to use the USB stick, unless your BIOS supports direct booting from USB.  Windows needs to be installed first.  Then partition your disk with GParted, etc., and install Ubuntu from the CD.  It will write grub to the MBR when it installs.

---

### Post by sidzen on 2010-11-08
" . . . and left a ntfs partition . . ."
Also --
"I love Ubuntu & I convert windoze people."

Convert and be Pane-free!

---

### Post by cacycleworks on 2010-11-08
> **cybergnome said:**
> The windows installation CD by default uses the entire disk and overwrites the MBR.  If grub was installed to the MBR, it's gone, and you won't be able to use the USB stick, unless your BIOS supports direct booting from USB.  Windows needs to be installed first.  Then partition your disk with GParted, etc., and install Ubuntu from the CD.  It will write grub to the MBR when it installs.

Yes... BIOS boots to USB, as mentioned above. It boots to Slitaz linux no problem. It boots but fails during install at the detect hardware phase when installing ubuntu. It fails to start liveCD version of ubuntu.

This computer can start up Knoppix from the CD. It also fails during installation of ANY ubuntu CD I try.

---

### Post by cacycleworks on 2010-11-08
Update: Tried the RAM in different locations and now the installer gets past partitioning and then the world turns red and the "[!!] Install the base system" window popsup. Base system installation error The Debootstrap program exited with an error (return value 1). Check /var/log/syslog or see virtual console 4 for the details.
<Go Back> <Continue>

Alt-F4 ... last few lines are:
```

Nov 8 17:47:31 main-menu[421]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Nov 8 17:47:31 main-menu[421]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Nov 8 17:47:31 main-menu[421]: INFO: Falling back to the package description for console-setup-udeb
Nov 8 17:47:31 main-menu[421]: INFO: Falling back to the package description for console-setup-udeb
(note: the above 4 lines repeat for every menu item selected)
Nov 8 17:47:31 main-menu[421]: INFO: Menu item 'bootstrap-base' selected
Nov 8 17:47:31 apt-install: Queueing package console-setup for later installation
Nov 8 17:47:38 debootstrap: tar: invalid tar magic

```

---

### Post by cacycleworks on 2010-11-08
Ah good times. Lowered the overclock and it works.

---

### Post by cybergnome on 2010-11-08
I would think you have a hardware issue other than the installation drive, except for the fact that you say you had Ubuntu working at one point.  You might want to remove all drive connections, SATA, ide and usb, and see if the CDs will boot.  If not, then there would appear to be another hardware conflict.

If they do boot, then the disconnected installation drive may be grunged and need to be wiped clean.

Can't think of anything else. :confused:

---

