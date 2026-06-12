---
title: "Fresh XP / 10.10 Dual Boot Install - Blinking Cursor After XP Choice from Grub"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by Rendrago on 2010-10-26
I originally replied to a thread over in Absolute Beginners Talk but decided to post my own over here.

[http://ubuntuforums.org/showthread.php?t=1603380]("http://ubuntuforums.org/showthread.php?t=1603380")

I've done this twice now with my dad's PC.

I install Windows XP Professional SP2 from CD that I have used on many other computers. I reboot and Windows works just fine. I then insert the Ubuntu 10.10 32-bit desktop install CD and reboot. I start the install and choose to install along side Windows (dual boot) with all the default options. Everything goes fine and Ubuntu works. If I reboot and choose XP Pro from the grub menu, I get a blinking cursor on a black screen.

Both work independently of each other, just not in a dual-boot environment.

I've done the XP recovery fixboot and then an update-grub from Ubuntu. Same deal.

I wiped the drive with zeros and checked for bad sectors. I ran memtest and found no errors.

I found this thread:

[http://ubuntuforums.org/showthread.php?t=1393848](http://ubuntuforums.org/showthread.php?t=1393848)

Could it be the mysterios hidden BIOS area in this crappy Compaq?

Testdisk shows this:

```
Disk /dev/sda - 200 GB / 186 GiB - ATA ST3200822A

Hidden sectors are present.

size       390721968 sectors
user_max   390721968 sectors
dco        390721968 sectors
Device Configuration Overlay (DCO) present.
```

```
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63

     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 12160   0 32  195350369
 2 E extended             12160   2  1 24321  74  9  195371010
 5 L Linux                12160   2  3 24130  49 47  192301056
   X extended             24130  49 48 24321  74  9    3069952
 6 L Linux Swap           24130  82 17 24321  74  9    3067904
```

```
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 12160   0 32  195350369

Boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.



[  Quit  ]  [  List  ]  [Org. BS ]  [Rebuild BS]  [  Dump  ]
```

I am using all the original hardware as follows:

Athlon XP (B) 3200+ 2.2 GHz, 400 MHz Front side bus, Socket A
Chipset Via KM400A
MB: Asus A7V8X-LA
Compaq motherboard name: Kelut-GL6E
VIA UniChrome graphics (Integrated with up to 64 MB allocated video memory)
Memory Installed: 512 MB (1 X 512) 184 pin, DDR SDRAM
Hard drive: 200 GB 7200 rpm (Seagate Barracuda ST3200822A

Link to the manufacturer spec page:

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=ca&docname=c00280664&product=443740&dlc=en&lang=en]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=ca&docname=c00280664&product=443740&dlc=en&lang=en")

I can certainly move to an earlier version but I don't usually like to let these things go without knowing why. Ideas anyone?

Thanks!

---

### Post by wilee-nilee on 2010-10-26
Not sure but if your letting the install partitioner resize XP then install Ubuntu this may be the problem.

The basic drill is Install XP either to a custom sized partition, leaving a unallocated for Linux. The other method would be to resize XP with a partitioner like gparted on the live cd, then rebooting windows to make sure it works. then install in the unallocated space or build your own Linux setup.

Have you tried a chkdsk check on any of the XP installs?, you can do it from a install cd or if you can get to the safe command line mode in XP with a f8 prompt on choosing XP at boot possibly.

---

### Post by Rendrago on 2010-10-26
I am letting the Ubuntu install partitioner resize the NTFS partition. I can certainly try all of this over again with two pre-created partitions with G-Parted. Or with Windows leaving some space as you suggest. I was just hoping my Dad could try this with the normal XP install and the Ubuntu CD and not have to jump through any hoops (I'm trying to teach him the whole install process). I guess a challenge is a good way to teach.

XP doesn't attempt to boot at all so no F8. Through the XP recovery console, "CHKDSK found one or more errors on the volume". A CHKDSK /R is taking CONSIDERABLY longer. More to come...

---

### Post by wilee-nilee on 2010-10-26
> **Rendrago said:**
> I am letting the Ubuntu install partitioner resize the NTFS partition. I can certainly try all of this over again with two pre-created partitions with G-Parted. Or with Windows leaving some space as you suggest. I was just hoping my Dad could try this with the normal XP install and the Ubuntu CD and not have to jump through any hoops (I'm trying to teach him the whole install process). I guess a challenge is a good way to teach.

XP doesn't attempt to boot at all so no F8. Through the XP recovery console, "CHKDSK found one or more errors on the volume". A CHKDSK /R is taking CONSIDERABLY longer. More to come...

There is a custom install option on the XP cd that will allow you to make the partition the size you want and install to it, leaving a unallocated space. You just have to know the MB breakdown I think the custom install partitioner runs in MB. 

The easiest way though may be just install XP, make sure its working then shrink it with gparted. Reboot to let it run a auto chkdsk, generally it will automatically run this. Make sure it works then install in the open unallocated space with the Ubuntu cd.

Make sure as well that you set the XP up with a limited account to run from, this actually is purported to wipe out about 90% of the dangers on the web. the other 10% though is everywhere, so act accordingly. You can run most things as a admin from a limited account by right clicking and running as admin . Of course both accounts should have strong passwords.

---

### Post by Rendrago on 2010-10-26
CHKDSK /R found no errors but I still can't boot into Windows. Ubuntu boots fine.

I guess in addition to looking for a fix I was also looking for an answer as to why this would happen with a clean install? I'll certainly re-install again with your suggestions tomorrow night and post the results (-5 EST).

Thanks for your assistance!

---

### Post by wilee-nilee on 2010-10-26
> **Rendrago said:**
> CHKDSK /R found no errors but I still can't boot into Windows. Ubuntu boots fine.

I guess in addition to looking for a fix I was also looking for an answer as to why this would happen with a clean install? I'll certainly re-install again with your suggestions tomorrow night and post the results (-5 EST).

Thanks for your assistance!

I wasn't sure where your at, but run the bootscript in my signature then post the resulting text in code tags. Just click on the # in the reply you will see the tags appear and put the code in between. 

At the least this script is good for any user once you understand all the information. I use it all the time when partitions have changed due to installs to confirm what is where.

---

### Post by Rendrago on 2010-10-26
The Kingston drive is just what I'm using to move info back and forth from my Dad's PC (the one in question) to my main box.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   195,350,431   195,350,369   7 HPFS/NTFS
/dev/sda2         195,350,526   390,721,535   195,371,010   5 Extended
/dev/sda5         195,350,528   387,651,583   192,301,056  83 Linux
/dev/sda6         387,653,632   390,721,535     3,067,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3CF42AA1F42A5D80                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        df13b81d-50f7-4a14-b4c2-5eb84831017e   ext4                                     
/dev/sda6        9dd18c12-2ca3-46f7-a57b-83a30b87179a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         54B0F2FDB0F2E480                       ntfs       KINGSTON 16GB                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb         /media/KINGSTON 16GB     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set df13b81d-50f7-4a14-b4c2-5eb84831017e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set df13b81d-50f7-4a14-b4c2-5eb84831017e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set df13b81d-50f7-4a14-b4c2-5eb84831017e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=df13b81d-50f7-4a14-b4c2-5eb84831017e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set df13b81d-50f7-4a14-b4c2-5eb84831017e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=df13b81d-50f7-4a14-b4c2-5eb84831017e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set df13b81d-50f7-4a14-b4c2-5eb84831017e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set df13b81d-50f7-4a14-b4c2-5eb84831017e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3cf42aa1f42a5d80
	drivemap -s (hd0) ${root}
	chainloader +1
}
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=df13b81d-50f7-4a14-b4c2-5eb84831017e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9dd18c12-2ca3-46f7-a57b-83a30b87179a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 108.8GB: boot/grub/core.img
 151.7GB: boot/grub/grub.cfg
 100.8GB: boot/initrd.img-2.6.35-22-generic
 108.8GB: boot/vmlinuz-2.6.35-22-generic
 100.8GB: initrd.img
 108.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  18 ee 90 7c 70 05 91 7c  ff ff ff ff 6d 05 91 7c  |...|p..|....m..||
00000010  78 01 07 00 00 00 07 00  00 00 00 00 78 73 09 00  |x...........xs..|
00000020  a0 e9 06 00 01 6b 09 00  f0 d8 ff ff ff ff ff ff  |.....k..........|
00000030  18 ea 06 00 b8 7f 09 00  40 49 03 01 41 00 00 00  |........@I..A...|
00000040  e3 ac 02 01 00 00 00 00  28 eb 06 00 00 00 00 00  |........(.......|
00000050  fc 14 00 01 0b 00 00 00  b0 7f 09 00 68 01 07 00  |............h...|
00000060  00 00 00 00 00 00 00 00  b0 7f 09 00 08 02 00 00  |................|
00000070  b8 7f 09 00 c8 05 91 7c  78 01 07 00 08 02 00 00  |.......|x.......|
00000080  51 05 00 00 00 00 07 00  78 e7 06 00 a8 f8 06 00  |Q.......x.......|
00000090  ff ff ff ff 18 ee 90 7c  f0 06 91 7c ff ff ff ff  |.......|...|....|
000000a0  eb 06 91 7c ec 30 01 01  00 00 07 00 00 00 00 00  |...|.0..........|
000000b0  00 02 00 00 00 02 00 00  d8 37 07 00 00 00 00 00  |.........7......|
000000c0  00 00 07 00 00 00 00 00  50 00 00 00 01 00 00 00  |........P.......|
000000d0  c8 00 06 01 58 30 07 00  fc 14 00 01 a8 24 07 00  |....X0.......$..|
000000e0  00 00 00 00 00 00 00 00  c8 03 00 00 00 00 00 00  |................|
000000f0  fc 14 00 01 e8 29 07 00  00 00 00 00 00 00 00 00  |.....)..........|
00000100  00 00 00 00 0c ea 06 00  10 ea 06 00 00 00 00 00  |................|
00000110  c8 05 91 7c 60 73 09 00  dc ea 06 00 51 05 91 7c  |...|`s......Q..||
00000120  e8 06 07 00 6d 05 91 7c  4a 00 00 00 f8 00 06 01  |....m..|J.......|
00000130  02 00 00 00 00 00 00 00  ff ff ff ff 18 ee 90 7c  |...............||
00000140  70 05 91 7c ff ff ff ff  6d 05 91 7c 95 31 01 01  |p..|....m..|.1..|
00000150  00 00 07 00 00 00 00 00  0c eb 06 00 2b c2 02 01  |............+...|
00000160  00 00 00 00 e4 ea 06 00  01 00 00 00 40 49 03 01  |............@I..|
00000170  28 eb 06 00 36 1e 02 01  4a 00 00 00 a8 f8 06 00  |(...6...J.......|
00000180  58 00 00 00 10 00 00 00  48 2a 07 00 00 00 00 00  |X.......H*......|
00000190  00 ee 90 7c 00 00 00 00  00 00 00 00 00 00 00 00  |...|............|
000001a0  00 00 00 00 00 00 07 00  00 00 07 00 00 00 07 00  |................|
000001b0  48 2a 07 00 00 00 00 00  00 ff ff ff 00 00 00 fe  |H*..............|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 76 0b 00 fe  |...........Hv...|
000001d0  ff ff 05 fe ff ff 02 48  76 0b 00 d8 2e 00 00 00  |.......Hv.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Thanks again.

---

### Post by Rendrago on 2010-10-26
I'll take a guess and say the unknown boot loaded can't be good. When I first started over I used Darik's Boot and Nuke (quick). Maybe I should have done the long DOD rewrite of the drive? Or something else. Thought I'd take a guess before anyone replied...

---

### Post by wilee-nilee on 2010-10-26
> **Rendrago said:**
> I'll take a guess and say the unknown boot loaded can't be good. When I first started over I used Darik's Boot and Nuke (quick). Maybe I should have done the long DOD rewrite of the drive? Or something else. Thought I'd take a guess before anyone replied...

Are you referencing the unknown on sda2 the extended that is a normal reading so to speak. As far as I can tell the script looks as it should. Ubuntu is showing XP in the grub bootloader.

Since you have Ubuntu installed you probably can probably do a custom install with XP, and just have it install back to the same place.

I have done this as well it works, but takes as long as a standard install basically.
[http://lifehacker.com/191277/rebuild-xp-without-losing-data-or-reinstalling-software](http://lifehacker.com/191277/rebuild-xp-without-losing-data-or-reinstalling-software)

Edit: Have you tried just loading the ms bootloader to the mbr boot the XP cd I think you know how to get to the repair cli and run fixmbr and reboot and see if XP boots independently.

---

### Post by Rendrago on 2010-10-26
Awesome! I did not know you could do that. Dang poorly worded Windows install screens! I'll try it tomorrow and post a reply.

---

### Post by wilee-nilee on 2010-10-26
> **Rendrago said:**
> Awesome! I did not know you could do that. Dang poorly worded Windows install screens! I'll try it tomorrow and post a reply.

The XP disc and overall functions possible are not known by a lot of the public. The instructions for stuff is easy to find on the web if you know the correct words.

If you try the fixmbr method and XP boots up and runs, you can reload grub quite easily with the live Ubuntu cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Just wanted to leave you with a few more tools good luck.

---

### Post by Rendrago on 2010-10-28
I ran the Windows repair option and still no boot. I ran the fixmbr and still no boot. After trying dual boot three times now it's just not worth it to install Ubuntu on this crappy old Compaq machine. Ubuntu works on it. Windows XP works on it. They just don't play nice together. I'm sure I could have spent a few more days with this but my dad wants his PC back and my personal machine dual boots just fine with encryption and all the other nice bells and whistles that come with Ubuntu. Thanks for your help!

(I'd still love to know what caused all this though...)

---

### Post by wilee-nilee on 2010-10-28
> **Rendrago said:**
> I ran the Windows repair option and still no boot. I ran the fixmbr and still no boot. After trying dual boot three times now it's just not worth it to install Ubuntu on this crappy old Compaq machine. Ubuntu works on it. Windows XP works on it. They just don't play nice together. I'm sure I could have spent a few more days with this but my dad wants his PC back and my personal machine dual boots just fine with encryption and all the other nice bells and whistles that come with Ubuntu. Thanks for your help!

(I'd still love to know what caused all this though...)

I think if you had installed XP in a custom sized partition with its installer, or shrunk it then made sure it still boots you would have been fine. I think you got to caught up in trying to fix something that was not fixable, as you used the same method of installing both times. This makes it seem that it wont work in actuality it just may have been using a standardized process that was needed.

Your always asking for trouble in my opinion when you let the installer resize another OS to install another, especially when one is MS.

---

