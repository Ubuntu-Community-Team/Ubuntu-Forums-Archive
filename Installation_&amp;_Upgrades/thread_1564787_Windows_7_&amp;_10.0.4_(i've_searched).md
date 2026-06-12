---
title: "Windows 7 &amp; 10.0.4 (i've searched)"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by theOnlyJuan on 2010-08-31
I've searched and have had no luck finding specifically what I'm doing wrong here.
I have a 320gb laptop drive.  ~200gb is to windows 7; then I installed Ubuntu 10.0.4 to the 'rest' (~120gb) of the free drive space.  

Reboot and I get the grub error grub rescue prompt.
I tried reinstalling ; even trying the manual partitioning with no luck.
I booted w/ the live cd and [tried the repair process]("http://ubuntuforums.org/showthread.php?t=1014708") with no success (twice).

What is the appropriate procedure for installing Ubuntu this way?  Nothing talk about installing to free space on the same drive.  Is the procedure any different?  If so, what am I doing wrong?  Should I be installing to a 'primary' partition instead of an extended?

the -sudo fdisk -l (if I recall correctly) was [like this]("http://img517.imageshack.us/img517/713/svr8xil.jpg"); just different start, end, & blocks.

Thoughts on approaching this differently is appreciated.  I (am trying) have repaired it so I can boot win7 again, but am hesitant to try this again.

Cheers,
the juan

---

### Post by Mark Phelps on 2010-08-31
> **theOnlyJuan said:**
> What is the appropriate procedure for installing Ubuntu this way?  Nothing talk about installing to free space on the same drive.  Is the procedure any different?  If so, what am I doing wrong?  Should I be installing to a 'primary' partition instead of an extended?
From what you've said, you've done nothing wrong.  Ubuntu installs just fine to an Extended partition.

Would be better if you would post the ACTUAL output of sudo fdisk, not someone else's output.

>  ... so I can boot win7 again, 

If that is your immediate concern, boot from the Win7 Repair CD that you made and run startup repair three times.

In case you did NOT make such a CD, use the links below to download and burn the CD image:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by theOnlyJuan on 2010-08-31
Thanks for the reply.  I'm in a time pinch; so I purchased a new drive and installed win7 and am right now installing ubuntu again to see what happens.
If it all works; I'll hook up my old drive externally and copy over my files and be done with it.

I think I ran the window repair only twice; command line bootrec twice and using the automated startup repair twice.
Maybe third time is a charm?  
I may swap drives back and try it again just to see.  
I'll post the sudo output if I do this.

Thanks again.  It's appreciated.

---

### Post by theOnlyJuan on 2010-08-31
Where I'm at (with a new 320gb drive)
Install Win 7 (~200gb) partition
Installed ubuntu 10.0.4 (32bit) to rest of drive (~100gb) - choose the first partitioning option.  Says something about installing 'side by side'.

Reboot:
Grub error (again)  :(

Boot to live cd and sudo fdisk -l is:
[PHP]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7a43fd48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       20011   160628456    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           20011       38914   151838721    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           20011       38141   145632256   83  Linux
/dev/sda6           38141       38914     6205440   82  Linux swap / Solaris
ubuntu@ubuntu:~$ [/PHP]

Thoughts or feedback is appreciated.
edit: I'll be trying the repair from the live cd next.

---

### Post by theOnlyJuan on 2010-08-31
Ran the repair
[PHP]ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ [/PHP]

Reboot
error: no such partition.
grub rescue> _
:confused:

Recommendations?  Next Steps?

Hardware I'm working with:
HP Tablet TC4400.  USB to IDE/sata adapter (new) connected to dvd-rw drive (new also).  
Burned the ubuntu iso disc at 8x with verification.

---

### Post by theOnlyJuan on 2010-08-31
Further info.
I burned a new 10.0.4 disc (8x w/ verification) and reinstalled the the drive.
This time I choose to erase the entire contents of the drive; Ubuntu only.

Same thing.  
Grub Error.  This proves that it's not a dual boot issue...  I'm even more thoroughly confused.  

I'm tempted to try and install an older ubuntu distro...

---

### Post by varunendra on 2010-09-03
> **theOnlyJuan said:**
> Further info.
I burned a new 10.0.4 disc (8x w/ verification) and reinstalled the the drive.
This time I choose to erase the entire contents of the drive; Ubuntu only.

Same thing.  
Grub Error..
You mean you installed like [this]("http://www.ubuntu.com/desktop/get-ubuntu/download") (step 4 > Show me), chose to use '**entire drive**' and still '**grub error**'????

Is the cd working in Live mode? Have you verified its contents?

If yes to all :shock:, please boot into Live Session, download & run [Boot Info Script]("http://bootinfoscript.sourceforge.net/") (courtesy- Meierfra) and post back its result here.

---

### Post by theOnlyJuan on 2010-09-03
> **varunendra said:**
> You mean you installed like [this]("http://www.ubuntu.com/desktop/get-ubuntu/download") (step 4 > Show me), chose to use '**entire drive**' and still '**grub error**'????

Yes - I choose to use entire drive.  I agree, very strange indeed.  
> 
Is the cd working in Live mode? Have you verified its contents?

Cd works in live mode- was able to try and run the grub repair in the terminal.  
Verification?  Didn't realize I had to hit the 'any key' to get the boot menu to choose verification.  Ran w/ success.
> 
If yes to all :shock:, please boot into Live Session, download & run [Boot Info Script]("http://bootinfoscript.sourceforge.net/") (courtesy- Meierfra) and post back its result here.
Sounds like a great plan.  Since the last post, I had to drop Win 7 back on it and get my laptop back on the clock since it is part of me paying the bills.
I'll drop back in the other hard drive and start it all again (erase and install ubuntu).
Have any tools you recommend to 'prepare' the drive?  Like the old fdisk days? (not that I desire that again).  ;)

Thanks again for all the help.  I consider myself a step above a great geek and this has me stumped.  Glad it's not just me ...

-theOnlyJuan

---

### Post by theOnlyJuan on 2010-09-03
Booted to live cd - ran install - erase and installed.

reboot
Grub error : out of disk

Boot off live cd and ran suggested Boot Info Script.
Results:
[PHP]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009e124

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   604,774,399   604,772,352  83 Linux
/dev/sda2         604,776,446   625,141,759    20,365,314   5 Extended
/dev/sda5         604,776,448   625,141,759    20,365,312  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        cb273d57-1c55-4f7a-9c54-e0be17cc556d   ext4                                     
/dev/sda5        8854868c-b468-4488-937b-69e16503a755   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cb273d57-1c55-4f7a-9c54-e0be17cc556d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cb273d57-1c55-4f7a-9c54-e0be17cc556d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cb273d57-1c55-4f7a-9c54-e0be17cc556d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=cb273d57-1c55-4f7a-9c54-e0be17cc556d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cb273d57-1c55-4f7a-9c54-e0be17cc556d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=cb273d57-1c55-4f7a-9c54-e0be17cc556d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cb273d57-1c55-4f7a-9c54-e0be17cc556d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cb273d57-1c55-4f7a-9c54-e0be17cc556d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 174.0GB: boot/grub/core.img
 152.7GB: boot/grub/grub.cfg
 174.0GB: boot/initrd.img-2.6.32-24-generic
 174.0GB: boot/vmlinuz-2.6.32-24-generic
 174.0GB: initrd.img
 174.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  01 70 55 c0 b1 a3 c0 b5  be c0 00 c2 c0 06 a1 55  |.pU............U|
00000010  c0 00 42 c0 00 f3 c0 0c  cd c0 00 82 d5 c0 00 bc  |..B.............|
00000020  c0 58 9f c0 12 5c c0 1a  c0 54 55 c2 a9 4c c0 1a  |.X...\...TU..L..|
00000030  0d c0 1a 38 c0 31 ab ad  c0 08 78 c0 08 c1 71 63  |...8.1....x...qc|
00000040  c0 04 84 c0 09 ad c1 af  99 c0 01 c1 3c 43 c0 0a  |............<C..|
00000050  0c c0 05 55 c1 10 80 c0  09 4c c0 0b d0 c0 33 b6  |...U.....L....3.|
00000060  ad c0 14 74 c0 05 c1 b2  bb c0 08 c3 c0 51 a6 b3  |...t.........Q..|
00000070  c0 01 c0 50 40 c7 c0 01  d9 c0 0f 26 d5 c0 07 c0  |...P@......&....|
00000080  8a 00 ec c0 01 18 bd 08  00 a0 37 c0 00 47 bd 00  |..........7..G..|
00000090  60 00 50 bd 00 00 4d bd  00 40 69 c0 03 c0 15 c0  |`.P...M..@i.....|
000000a0  02 d7 c0 0b c0 cf 00 56  31 c0 09 c1 25 c0 c0 25  |.......V1...%..%|
000000b0  0f c0 31 58 55 c0 38 75  c0 00 83 c0 02 78 c0 01  |..1XU.8u.....x..|
000000c0  45 55 c0 01 3e 60 00 88  e0 1d ab 60 1f cc 4d 60  |EU..>`.....`..M`|
000000d0  00 ea 60 01 60 7e 40 94  e0 03 22 4d 60 03 04 60  |..`.`~@..."M`..`|
000000e0  00 60 24 00 54 e0 00 6b  55 60 00 7b 60 00 87 60  |.`$.T..kU`.{`..`|
000000f0  03 9f 60 00 c3 35 e0 05  d5 e0 05 dd 60 00 e0 00  |..`..5......`...|
00000100  c0 b5 35 e0 00 92 e0 02  6d 60 04 60 00 80 8c 53  |..5.....m`.`...S|
00000110  e0 00 60 28 c0 9a e0 02  8e 60 01 9b 55 60 03 90  |..`(.....`..U`..|
00000120  60 00 38 60 01 2e e0 1e  f8 33 60 1e 60 22 80 8e  |`.8`.....3`.`"..|
00000130  e0 15 e0 61 40 86 55 e0  15 7d 60 01 46 60 00 2f  |...a@.U..}`.F`./|
00000140  60 01 3a d5 e0 00 5a 60  00 8a 60 01 aa e0 1f 60  |`.:...Z`..`....`|
00000150  4a 04 00 d1 e0 00 f6 bc  00 a0 10 41 60 1f 25 bd  |J..........A`.%.|
00000160  00 e0 2a e0 1f 21 10 bd  00 80 19 e0 00 0e bd 00  |..*..!..........|
00000170  54 c0 fe e0 05 e6 60 04  d6 60 00 c9 b3 60 28 e0  |T.....`..`...`(.|
00000180  06 80 6f 60 02 61 48 2e  e0 08 aa 39 60 01 05 e0  |..o`.aH....9`...|
00000190  00 7e 60 0f cc e0 2f 6a  b6 e0 10 a7 60 00 9c 60  |.~`.../j....`..`|
000001a0  00 e1 84 87 75 e0 00 e3  60 49 24 60 14 e1 43 e0  |....u...`I$`..C.|
000001b0  23 80 9a 65 e0 1c 84 e0  01 60 1b 00 a5 e0 00 fe  |#..e.....`......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c0 36 01 00 00  |............6...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


[/PHP]

Thoughts?

---

### Post by oldfred on 2010-09-03
I cannot see anything out of place. Your boot script looks like any normal working install.

I am suspicious of a BIOS setting that is interfering. Usually those prevents installs?

Some things to look at:
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Raid meta data on drive - even if one drive (Vendor happened to set it on)
Search for Unique issue with your specific hardware.
See post #4 busybox exit & boot - blue screen;s post
[http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay)
busybox See quixote post
[http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay)
Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"

---

### Post by varunendra on 2010-09-03
> **theOnlyJuan said:**
> Booted to live cd - ran install - erase and installed.

reboot
[COLOR=Red]**Grub error : out of disk**[/COLOR]
....
....

Thoughts?
Now that you are in safe hands of oldfred, I think I'd only sit aside & watch the progress. :)

However, you may find these interesting:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)
(Note that I couldn't find those lines in 10_linux file as mentioned in above page. Those were only in grub.cfg)

[http://ubuntuforums.org/showthread.php?t=1523825](http://ubuntuforums.org/showthread.php?t=1523825)
(oldfred already knows this solved case, as he was involved in it)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477430](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477430)
(a solved bug)

Although given the efforts you've made so far, I highly doubt you haven't already come across these links.

I'll take my backseat now....):P

---

### Post by theOnlyJuan on 2010-09-03
My bios says F.04 version and the website shows F.09 ... and doesn't even list F.04... probably the problem.  

Current BIOS 2006; new (loading now) July 2008.

I'll let you know what happens once I reinstall.

IT'S WORKS!
I did not have to reinstall.

THE OFFICIAL FIX:
Update the bios[ from here.]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=1847962&swItem=ob-63517-1&prodNameId=1849071&swEnvOID=1059&swLang=8&taskId=135&mode=4&idx=1")

I'm a bit embarrassed- I should have known better.

Thanks for everyone's help.
John

---

