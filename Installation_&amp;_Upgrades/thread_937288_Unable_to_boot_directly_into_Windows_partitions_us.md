---
title: "Unable to boot directly into Windows partitions using GRUB"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by Mark Phelps on 2008-10-03
I'm trying to boot directly into each of my OS's from Grub.  While this works for the two Ubuntu OS's, it doesn't work for the two Windows OS's. Vista was installed after XP, so it created a boot menu and installed its boot files on the XP partition.

But I read recently (from caljohnsmith) that you COULD boot directly into the Windows partitions using GRUB. So, I copied the Vista boot files and directory from XP to Vista partition, modified my menu.lst file and booted.

No success -- still get the Vista menu.  Still have to select XP or Vista.

So, caljohnsmith, if you're still out there, could you please take a look at the stuff below and tell me what I'm doing wrong?

The first is the fdisk -l output.  There are three physical drives:(1) Ubuntu 7.10, (2) Ubuntu 8.04, (3)Windows (XP followed by Vista), but the fdisk below lists them as (1) Windows, (2) Ub untu 7.10, (3) Ubunto 8.04:

```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e47d8f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3134    25173823+   7  HPFS/NTFS
/dev/sda2   *        3135        7735    36957532+   7  HPFS/NTFS
/dev/sda3            7736       36481   230902245    5  Extended
/dev/sda5            7736       36481   230902213+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc55cc55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+  83  Linux
/dev/sdb2            9722        9964     1951897+  82  Linux swap / Solaris
/dev/sdb3            1217        5471    34178287+  83  Linux
/dev/sdb4            5472        9721    34138125    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb75111d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1216     9767488+  83  Linux
/dev/sdc2           14351       14593     1951897+  82  Linux swap / Solaris
/dev/sdc3            1217        4620    27342630   83  Linux
/dev/sdc4            4621       14350    78156225    c  W95 FAT32 (LBA)

Partition table entries are not in disk order
```

The menu.lst is below:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=45a0586e-3729-46ca-b902-428acfbbc234 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=792

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=45a0586e-3729-46ca-b902-428acfbbc234 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=45a0586e-3729-46ca-b902-428acfbbc234 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=af487234-fc61-4c44-ac49-fdf8ead1e9df ro splash vga=795 quiet
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=af487234-fc61-4c44-ac49-fdf8ead1e9df ro single
initrd		/boot/initrd.img-2.6.22-15-generic

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

# This entry added manually for Windows OSs
title		Windows OS Menu
map		(hd0) (hd2)
map		(hd2) (hd0)
rootnoverify	(hd2,0)
savedefault
chainloader +1

# This entry added manually for Vista
title		Vista Direct Boot
map		(hd0) (hd2)
map		(hd2) (hd0)
rootnoverify	(hd2,1)
savedefault
chainloader +1

# This entry added manually for PING boot
title		PING Recovery
root		(hd1,0)
kernel		/boot/kernel pxe init=/linuxrc root=/dev/ram0 rw noapic nolapic lba devfs=nomount ramdisk_size=33000 load_ramdisk=1 prompt_ramdisk=0
initrd		/boot/initrd.gz
```

Have added the Vista direct boot entry.  Tried changing the rootnoverify to (hd2,1) and (hd2,2).  The first (which SHOULD be Vista) results in the Windows OS Selection menu; the second results in a blank screen.  The other Windows boot entry (hd2,0) points to the XP partition and ALSO displays the Windows OS Selection menu.  Just can't find a way to get around that menu!!

---

### Post by caljohnsmith on 2008-10-03
> **Mark Phelps said:**
> 
Have added the Vista direct boot entry.  Tried changing the rootnoverify to (hd2,1) and (hd2,2).  The first (which SHOULD be Vista) results in the Windows OS Selection menu; the second results in a blank screen.  The other Windows boot entry (hd2,0) points to the XP partition and ALSO displays the Windows OS Selection menu.  Just can't find a way to get around that menu!!
Hi Mark, so when you get the "Windows OS Selection menu", can you then boot successfully into Vista or XP? From your description, it sounds like Grub may be booting Vista just fine, but all you need to do is modify the Vista boot menu. A really easy way to do that is with a program called [EasyBCD]("http://neosmart.net/dl.php?id=1"). Give that a shot and let me know how it goes. :)

---

### Post by Mark Phelps on 2008-10-04
Hi caljohnsmith ...  Thanks for getting back to me.

I can boot into the Windows OS selection menu, and from there to either XP or Vista.  I can also boot into the Ubuntu OSs without any problems.

What I was hoping to do was to be able to boot directly into Vista and to XP, each from separate GRUB menu selections -- and bypass the Windows OS menu.  That's what I thought you were doing. Maybe I misunderstood what you said in the other post ...

I hadn't used EasyBCD but I had used VistaBootPro, but aren't those for using the Windows boot to add other OS's?  That's the opposite of what I want to do.  I want to bypass the Windows boot and use GRUB to select the OSs.

---

### Post by caljohnsmith on 2008-10-04
> **Mark Phelps said:**
> Hi caljohnsmith ...  Thanks for getting back to me.

I can boot into the Windows OS selection menu, and from there to either XP or Vista.  I can also boot into the Ubuntu OSs without any problems.

What I was hoping to do was to be able to boot directly into Vista and to XP, each from separate GRUB menu selections -- and bypass the Windows OS menu.  That's what I thought you were doing. Maybe I misunderstood what you said in the other post ...

I hadn't used EasyBCD but I had used VistaBootPro, but aren't those for using the Windows boot to add other OS's?  That's the opposite of what I want to do.  I want to bypass the Windows boot and use GRUB to select the OSs.
Yes, definitely you can use Grub to directly boot into Vista or XP, but I don't know yet which partition contains the Vista boot files and which contains the XP boot files; you want to make sure that all of Vista's boot files are in its partition, and all of XP's boot files are in its partition so they can be independent of each other when you boot them. I believe you can use that EasyBCD to modify your Vista's boot menu so that you can boot directly into Vista from Grub, and not be offered any other boot choices from the Vista boot menu. In other words, Grub is booting Vista fine, but it is Vista that is giving you the extra OS choices in its boot menu, so you need to remove those OSes from the menu if you want to just boot directly into Vista from Grub. 

And about booting XP, you'll need to make sure that all of XP's boot files are in the XP partition's root directory like I mentioned, and not in Vista's partition:
```
boot.ini
NTDETECT.COM
ntldr
```
Once you are sure of the above files are in the XP root directory, you may have to do a "fixboot" and also rebuild the XP partition's boot sector with testdisk to get XP booting directly from Grub; before I give you specifics about that, can you let me know which partition on sda is Vista and which is XP? And if it is not too much trouble, can you give me a directory listing of the root directory of both the Vista and XP partitions after you've got their boot files in place? We can work from there. :)

---

### Post by Mark Phelps on 2008-10-04
OK, I understand -- you're saying remove the choices from the Vista boot menu and it will boot directly into Vista.  That makes sense.

As to the drives, the SATA drive contains both XP, and Vista, with XP being sda1 and Vista being sda2.  It also has its own MBR set up for Windows so that it can boot on its own.

The actual boot MBR is on the first PATA drive (sdb1) and it has its own GRUB.  But the working GRUB is on sdb2 -- the Ubuntu 8.04 drive.

As to messing with the MBR, let me think about how I want to proceed.  Right now, it's inconvenient, but it's not "broke".

Thanks for your help.

---

### Post by caljohnsmith on 2008-10-04
Well let me know if EasyBCD works for you so that you can boot directly into Vista from Grub without getting Vista's boot menu. Here is the XP entry you can add in Grub's menu.lst: 
```
title		Windows XP
rootnoverify	(hd2,0)
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader +1
```
Also, please do the following:
```
sudo umount /dev/sda1
sudo umount /dev/sda2
```
Don't worry about any "not mounted" errors from the above commands, it is just to make sure. Then do:
```
sudo mkdir /media/sda1 /media/sda2
sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sda2 /media/sda2
ls -l /media/sda1
ls -l /media/sda2
```
And post the output of the above commands.

P.S. If you want to see an example of how we helped someone in almost exactly your same position boot directly into Vista and XP from Grub (both XP and Vista were on the same HDD like you), see [this thread]("http://ubuntuforums.org/showthread.php?t=932727").

---

### Post by Mark Phelps on 2008-10-04
OK ... to continue ...

The XP entry looks like what I already have for the Windows OS menu entry but with the rootnoverify earlier.  So, I've changed it.

Did the umount/mount stuff.

Results of first ls -l:

```
bill@BWHeron:~$ ls -l /media/sda1
total 1573638
drwxrwxrwx 1 root root          0 2006-01-20 14:50 abu
drwxrwxrwx 1 root root          0 2006-10-09 13:49 ATI
-rwxrwxrwx 1 root root        189 2006-01-16 14:25 audio.log
drwxrwxrwx 1 root root       4096 2008-03-28 23:11 Boot
-rwxrwxrwx 1 root root        379 2007-02-09 19:01 Boot.BAK
-rwxrwxrwx 1 root root        379 2007-02-09 19:07 boot.ini
-rwxrwxrwx 1 root root     333203 2008-01-19 02:45 bootmgr
-rwxrwxrwx 1 root root       8192 2007-02-09 19:01 BOOTSECT.BAK
drwxrwxrwx 1 root root          0 2006-01-20 20:26 BOOTWIZ
-rwxrwxrwx 1 root root          0 2006-01-16 14:00 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2006-01-16 15:00 Documents and Settings
drwxrwxrwx 1 root root          0 2008-01-01 12:35 Downloads
drwxrwxrwx 1 root root          0 2006-03-20 22:37 epson
drwxrwxrwx 1 root root          0 2006-03-18 15:52 EPSONREG
-rwxrwxrwx 1 root root          0 2006-01-16 14:00 IO.SYS
-rwxrwxrwx 1 root root          0 2006-01-16 14:00 MSDOS.SYS
drwxrwxrwx 1 root root          0 2006-03-05 13:18 My Documents
drwxrwxrwx 1 root root          0 2007-08-14 20:26 NST
-rwxrwxrwx 1 root root      47564 2004-08-04 08:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250032 2004-08-04 08:00 ntldr
drwxrwxrwx 1 root root          0 2006-11-26 13:23 NVIDIA
-rwxrwxrwx 1 root root 1610612736 2008-05-15 20:41 pagefile.sys
drwxrwxrwx 1 root root      28672 2007-04-01 13:41 Program Files
drwxrwxrwx 1 root root       4096 2006-03-19 11:19 PSADMIN
drwxrwxrwx 1 root root       4096 2007-02-11 13:30 $RECYCLE.BIN
drwxrwxrwx 1 root root          0 2006-01-21 01:31 RECYCLER
drwxrwxrwx 1 root root          0 2006-09-27 21:42 Softpaq
drwxrwxrwx 1 root root      20480 2008-10-03 20:28 System Volume Information
drwxrwxrwx 1 root root          0 2006-10-17 20:20 Temp
drwxrwxrwx 1 root root      77824 2008-05-15 20:44 WINDOWS
-rwxrwxrwx 1 root root         29 2007-01-06 15:39 wizard.txt
```

results of second ls -l:

```
bill@BWHeron:~$ ls -l /media/sda2
total 3575680
drwxrwxrwx 1 root root          0 2007-02-09 22:44 ATI
drwxrwxrwx 1 root root       4096 2008-03-28 23:11 Boot
-rwxrwxrwx 1 root root     333203 2008-01-19 02:45 bootmgr
-rwxrwxrwx 1 root root    3170304 2006-09-18 13:45 boot.sdi
drwxrwxrwx 1 root root          0 2008-09-19 14:01 Config.Msi
drwxrwxrwx 1 root root          0 2006-11-02 08:00 Documents and Settings
drwxrwxrwx 1 root root          0 2007-12-24 14:17 Drivers
drwxrwxrwx 1 root root          0 2008-03-08 03:53 epson
-rwxrwxrwx 1 root root          0 2007-02-13 20:56 IO.SYS
-rwxrwxrwx 1 root root     200257 2008-10-04 05:02 logfile
-rwxrwxrwx 1 root root          0 2007-02-13 20:56 MSDOS.SYS
drwxrwxrwx 1 root root          0 2007-02-10 23:47 MSOCache
drwxrwxrwx 1 root root          0 2007-06-01 21:20 NST
-rwxrwxrwx 1 root root     262144 2007-04-01 14:27 ntuser.dat
-rwxrwxrwx 2 root root      65536 2007-03-10 12:57 ntuser.dat{93019596-cf24-11db-8134-0015f27fe52e}.TM.blf
-rwxrwxrwx 2 root root     524288 2007-03-10 12:57 ntuser.dat{93019596-cf24-11db-8134-0015f27fe52e}.TMContainer00000000000000000001.regtrans-ms
-rwxrwxrwx 2 root root     524288 2007-03-10 12:57 ntuser.dat{93019596-cf24-11db-8134-0015f27fe52e}.TMContainer00000000000000000002.regtrans-ms
-rwxrwxrwx 2 root root      65536 2007-04-01 14:25 ntuser.dat{effc8e8c-e079-11db-a4a6-0015f27fe52e}.TM.blf
-rwxrwxrwx 2 root root     524288 2007-04-01 14:25 ntuser.dat{effc8e8c-e079-11db-a4a6-0015f27fe52e}.TMContainer00000000000000000001.regtrans-ms
-rwxrwxrwx 2 root root     524288 2007-04-01 14:25 ntuser.dat{effc8e8c-e079-11db-a4a6-0015f27fe52e}.TMContainer00000000000000000002.regtrans-ms
-rwxrwxrwx 2 root root       5120 2007-04-01 14:27 ntuser.dat.LOG1
-rwxrwxrwx 2 root root          0 2007-03-10 12:57 ntuser.dat.LOG2
drwxrwxrwx 1 root root          0 2008-06-21 16:10 NVIDIA
-rwxrwxrwx 1 root root 3534303232 2008-10-04 04:56 pagefile.sys
drwxrwxrwx 1 root root          0 2008-03-28 22:58 PerfLogs
drwxrwxrwx 1 root root       8192 2008-09-18 23:33 ProgramData
drwxrwxrwx 1 root root      24576 2008-08-30 15:16 Program Files
drwxrwxrwx 1 root root       4096 2007-02-11 13:30 $Recycle.Bin
drwxrwxrwx 1 root root          0 2007-02-09 20:50 RECYCLER
drwxrwxrwx 1 root root      12288 2008-10-03 20:28 System Volume Information
drwxrwxrwx 1 root root       4096 2007-06-01 16:06 Users
drwxrwxrwx 1 root root      36864 2008-09-19 14:02 Windows
drwxrwxrwx 1 root root          0 2008-05-20 20:38 winreimage
drwxrwxrwx 1 root root          0 2008-05-20 20:30 winremount
-rwxrwxrwx 1 root root  120889431 2008-05-20 20:51 winre.wim
```

You'll see the boot directory and related files in both partitions because Vista wrote them into the XP (first) partition upon installation, and after reading your post, I copied them into the second (Vista) partition.

Haven't had time to do the BCD edit stuff yet.

---

### Post by caljohnsmith on 2008-10-05
OK, it looks like the next step would be to delete the Vista boot files in the Win XP partition sda1 since you have them back in place in Vista's partition. Before you do that though, we need to check if Vista is still using those boot files in sda1 instead of its own partition, which is probably the case; when you are in Ubuntu do the following:
```
sudo grub
grub> device (hd0) /dev/sda
grub> hide (hd0,0)
grub> quit
```
That will change Win XP on sda1 to "hidden NTFS" so that Vista on sda2 should not be able to access sda1. Reboot, and if you *can't* boot successfully into Vista, we will know that Vista is still trying to use its boot files in XP's sda1 partition. If that is the case, then while sda1 is still hidden, boot your Vista Recovery CD and run:
```
bootrec /fixboot
```
That should fix the Vista partition's boot sector so that it points to the Vista partition for its boot files instead of the XP partition. Reboot and check if it worked. 

Once you can successfully boot into Vista while sda1 is still hidden, then we can safely delete Vista's boot files from sda1. So while you are in Ubuntu, first unhide sda1:
```
sudo grub
grub> device (hd0) /dev/sda
grub> unhide (hd0,0)
grub> quit
```
Then go ahead and delete the /boot folder and "bootmgr" file from your Win XP partition sda1. After that see if you can boot Win XP, and if not, boot your Win XP Install CD and run:
```
fixboot <drive letter>
```
Make sure you use the correct drive letter for the XP partition; you can get a list of drives with the "map" command. Let me know how it goes or if you run into problems.

---

### Post by Mark Phelps on 2008-10-05
OK, some progress ...

Hid the XP volume.  Able to boot into Vista using the Windows OS Menu. Not able to boot into XP -- get BSOD.  So, this looks like the Vista is using the boot files I copied over from the XP volume.

EasyBCD doesn't work, though.  Downloaded the latest version (haven't used it in a while) and when the XP volume is hidden, it fails.  Looks like it's trying to use the XP volume. So, I uhid the XP partition and made a trivial change to the boot menu using EasyBCD and saved it.  Then, changed the menu.lst entry to boot into the Vista partition and -- tad da!!  That entry brings up the modified Vista boot menu!  So, it looks like it IS booting into the Vista partition.

But, in the process, I used EasyBCD to add an entry to the Vista boot menu for WinRE.  Could never get that to work manually, so was never able to repair Vista.  Now, it works!

I'm going to play around with GRUB and see if I can boot into Win RE directly -- THAT should be interesting.

---

