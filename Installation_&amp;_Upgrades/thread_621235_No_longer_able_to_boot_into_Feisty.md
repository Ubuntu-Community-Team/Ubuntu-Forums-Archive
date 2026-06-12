---
title: "No longer able to boot into Feisty"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by SimonFitz on 2007-11-23
This is a long post but I wanted to supply details, and thanks in advance to any who respond!

Back in August I successfully installed Feisty on an external USB drive so that I could dual boot with Windows XP on my internal drive. With the help of the volumes of useful information in this website and others, I was able to partition the USB drive to create three extra partitions (root, home, swap) and install Feisty. Grub was installed, but I had problems booting from USB (couldn't find an option in the BIOS for my "ASUS A7N8X2.0 Deluxe ACPI BIOS Rev 1004" that actually worked) combined with "NTLDR is missing" errors so I eventually ended up using the Windows BootPart program.

Prior to a couple of weeks ago, my boot process was using Windows Boot.INI with the options of 'XP', 'Recovery Console' and 'Feisty'. Choosing the 'Feisty' option loaded Grub, and from Grub I could go into Feisty itself. Yes, convoluted and probably not the most efficient, but it worked - and I know to stop fiddling with computers when they basically do what I want!

However, in the last couple of weeks I have had the occasional "CMOS Checksum Error" messages when turning the computer on. Some of the BIOS settings changed (reset presumably) and the system time was no longer correct (although the date was). I was definitely able to still boot into Feisty when this first happened because I checked to see if the incorrect system time was a Windows XP issue (it wasn't). I suspect a dying motherboard battery, but this error message hasn't appeared for a while.

Suddenly though, I am now no longer able to boot into Feisty, and I far as I know nothing else has changed. Choosing the 'Feisty' option from Boot.Ini gives me a BootPart error message of "Cannot load from harddisk"  - I don't get anywhere near Grub!

I can boot using the LiveCD so I have run the usual commands for reference.

Fdisk gives:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         319     2562336   1c  Hidden W95 FAT32 (LBA)
/dev/hda2   *         320       14946   117491377+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1                  1       14711   118166076    c  W95 FAT32 (LBA)
/dev/sda2           30147       30401      2048287+  82  Linux swap / Solaris
/dev/sda3           14712       30146   123981637+   5  Extended
/dev/sda5           14712       28819   113322478+  83  Linux
/dev/sda6           28820       30146    10659096   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End          Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS
```

Disk hda is my internal drive, with a vendor created hidden partition and a main XP partition (my C drive in XP). Disk sda is my first external USB drive partitioned into a FAT32 drive (sda1 aka my G drive in XP), a swap drive (sda2), my home drive (sda5) and a root/boot drive (sda6). Not sure where sda4 is! Disk sdb is my second external USB drive which is entirely Windows NTFS (my F drive in XP).

My Grub menu.lst is

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=42a0a26d-86a4-4dd8-8c5c-9380c6ed7ac3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,5)

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
# defoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=42a0a26d-86a4-4dd8-8c5c-9380c6ed7ac3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=42a0a26d-86a4-4dd8-8c5c-9380c6ed7ac3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=42a0a26d-86a4-4dd8-8c5c-9380c6ed7ac3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=42a0a26d-86a4-4dd8-8c5c-9380c6ed7ac3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
chainloader	+1

```

Device.map is:

```
(hd0)	/dev/hda
(hd1)	/dev/sda
```

and I have also run these Grub commands:

```
grub> find /boot/grub/stage1
 (hd1,5)
```
```
grub> geometry (hd0)
drive 0x80: C/H/S = 14946/255/63, The number of sectors = 240121728, /dev/hda
   Partition num: 0,  Filesystem type is fat, partition type 0x1c
   Partition num: 1,  Filesystem type unknown, partition type 0x7


grub> geometry (hd1)
drive 0x81: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sda
   Partition num: 0,  Filesystem type is fat, partition type 0xc
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83


grub> geometry (hd2)
drive 0x82: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7
```

My Boot.Ini file is:
```

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\ubuntu.bin="Ubuntu 7.04 (Feisty Fawn)"
```

(I have recreated the "ubuntu.bin" file using BootPart but it was exactly the same.)

Does anyone have any suggestions as to what I can do to boot? Would attempting to install Grub to my internal drive be the easiest solution? Posts from Herman and others seem understandable but my hacked together efforts did use to work! Any thoughts gratefully received!

Simon

---

### Post by john_spiral on 2007-11-23
Have you re-installed your 'Windows BootPart' installation?

If you boot off the Ubuntu CD are all your drives including the external one visible?

Johne

---

### Post by SimonFitz on 2007-11-23
Johne - thanks and to answer your questions,

(1) Not sure I understand - with BootPart ([http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)), I create a copy of the bootsector and Window's Boot.Ini references it. Can't remember if this is the actual post I originally followed, but [http://ubuntuforums.org/showpost.php?p=507650&postcount=2](http://ubuntuforums.org/showpost.php?p=507650&postcount=2) was something like it. Recreating this file made no difference as the new file was the same (I compared them in a hex editor).

(2) When I boot from the LiveCD all my partitions on all my drives, internal and external, are visible right from the start - icons are on the desktop.

Something that I've only just noticed is that in my fdisk output there is no indication of a bootable partition on 'sda', unlike the others (and I've never even tried to boot from my second external USB). I seem to recall that the GParted LiveCD has the ability to make a partition bootable - could this be a solution?

Simon

---

### Post by john_spiral on 2007-11-24
Try gparted:

Partition -> manage flags 

and set the relevant Linux partition to bootable.

come back to us

---

### Post by SimonFitz on 2007-11-24
I've set my root partition (sda6) to be bootable using the GParted LiveCD but no joy - still the same error message. I don't know if this partition was ever set to be bootable though - when things are eventually workng (maybe a clean install to 7.10?) I'm going to write down on paper all my settings just in case!

---

### Post by Pumalite on 2007-11-24
Try changing the boot order of the hard drives. Let's see what happens.

---

### Post by meierfra on 2007-11-24
> Disk sdb is my second external USB drive which is entirely Windows NTFS (my F drive in XP).
Did you always have this drive or did you add it recently? Try booting with sdb unplugged.

---

### Post by SimonFitz on 2007-11-24
Pumalite - I've changed the order of boot devices in my BIOS but no luck. I've gone through having "CDROM" as the first boot device with either "USB-FDD", "USB-ZIP", "USB-CDROM" or "USB-HDD" as second (and "HDD-0" remaining as third), and also having the USB options first with "CDROM" second. Or have I misunderstood your reply - did you mean modifying my Boot.Ini file?

meierfra - I've had my second external USB drive (sdb aka F: ) since before installing Ubuntu. I have unplugged it but no difference!

Would it be easier for me to (attempt to!) install Grub onto my internal drive? The instructions I would follow are [http://ubuntuforums.org/showpost.php?p=3748949&postcount=2](http://ubuntuforums.org/showpost.php?p=3748949&postcount=2).

Thanks

Simon

---

### Post by Pumalite on 2007-11-24
That's what I would do. Grub is a much better boot loader than the one in Windows.

---

### Post by SimonFitz on 2007-11-24
Okay, now it's really gone wrong!

I followed the instructions in the post I referred to earlier but upon reboot the computer displayed the Grub message "Error 21". I had entered the following commands into a terminal:

```
sudo grub

find /boot/grub/stage1  --> returned (hd1,5)
root (hd1,5) --> no message good or bad after hitting enter
setup (hd0) --> mentioned embedding 17 sectors
quit
```

Whilst I was waiting for the LiveCD to boot, I remembered that "hd0" had two partitions - the vendor created 'recovery' (hda1) and my XP drive with Boot.Ini / NTLDR etc (hda2). I then entered the code above again, only this time with ```
setup (hd0,1)
``` This time there was mention of failures that were not fatal (stupidly I didn't record them). Rebooted and again got the error 21 message.

I read through various pages/threads on this error message (inc [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)) but I can't see anything I can do. It seems that using the "Super Grub Disk" can solve this sort of thing, but I'm not going to have access to a reliable CD writer for a few days.

Any suggestions?

Simon

---

### Post by Pumalite on 2007-11-24
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by SimonFitz on 2007-11-24
I've read that page, but I'm not sure what to do from it.

My menu.lst entries (full copy in my first post) for the Ubuntu kernels have "root (hd1,5)" which is what "find /boot/grub/stage1" returns.

If it seems I have to use "Super Grub Disk" then i'll have to wait a few days to use the computer ...

---

### Post by john_spiral on 2007-11-24
boot off a Linux CD.

sudo mount /dev/sda6 /mnt

sudo /mnt/usr/sbin/grub

this will take you to the grub menu, enter the below commands at the grub command prompt (only enter stuff in green):

grub> [COLOR="SeaGreen"]root (hd1,5)[/COLOR]
grub> [COLOR="SeaGreen"]setup (hd1) (hd1,5)[/COLOR]

Funnily enough all of the above stuff is from this months Linux Format mag (**When Linux Won't Boot**). 

The key command here is **setup (hd1) (hd1,5)** which tells Grub to re-install the original stage 1 grub into the MBR of hd1, and copies the original stage 1.5 grub into the sectors immediately following .

This will hopefully allow your Windows bootloader to load the grub bootloader on your 2nd disk (hd1).

give it a try.

Johne

---

### Post by meierfra on 2007-11-24
Check your bios and 
make  sure that the internal drive is first in the boot order , the ubuntu drive second and your other external drive last

> This time there was mention of failures that were not fatal (stupidly I didn't record them). 
One always gets this error message when  grub is installed to a partition rather than the MBR. So that is nothing to worry about.

---

### Post by meierfra on 2007-11-24
Follow my suggested first. If it didn't work, follow john_spirals suggestions. (johns_spirals suggestion should get you to the grub-menu at boot-up. But you will also have to edit menu.lst to boot into ubuntu)

---

### Post by SimonFitz on 2007-11-24
Johne - below is what happened, which hopefully will work ...

```
grub> root (hd1,5)

grub> setup (hd1)(hd1,5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,5)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
```


meierfra - reassuring to hear those error messages don't mean I've made things worse! I will have a look at the BIOS boot order again if the above doesn't work, although I don't have any options to choose specific external USB drives.

Off to reboot now - fingers crossed!

Simon

---

### Post by SimonFitz on 2007-11-24
Well, that didn't work - same error message as before ... "Grub loading stage 1.5." and then "Grub loading, please wait..." and then "Error 21". Didn't get to the Grub menu,

Sorry meierfra but I didn't see your subsequent message until now. I will change my BIOS boot order to internal hard drive, cdrom and then usb-hdd and see what happens.

Cheers

---

### Post by SimonFitz on 2007-11-24
I've gone through multiple combinations of boot order now without success - having hdd-0 first with cdrom second and usb-hd third, then usb-hd second and cdrom third, and then cdrom first with hdd-0 second ... etc etc ... all result in Grub error 21, as did having hdd-0 on its own with the other two disabled.

Trying usb-hd on its own resulted in this mesage: "disk boot failure, insert system disk and press enter".

As it is now quite late my time, I'll be off line for several hours. Any more suggestions in the meantime gratefully received, even if they involve junking Ubuntu to get Windows back - only as a short term solution of course!

Thanks

Simno

---

### Post by Pumalite on 2007-11-24
You can use Super Grub to restore MBR in Windows.

---

### Post by meierfra on 2007-11-24
1) If you aren't sick of trying things which probably won't work

Boot from the live CD, open a terminal and type

```
gedit mydevice.map 
```

This will open an empty file.

Add these lines to the file:

(hd0)  /dev/hda
(hd1) /dev/sdb
(hd2) /dev/sda

Save the file.  Go back to the  terminal:

```
sudo grub --device-map=mydevice.map
```

At the grub prompt

```

root (hd2,5)
setup (hd0)
quit

```

Edit your menu.lst:

```
mkdir ubuntu
sudo mount -t ext3 /dev/sda6 ubuntu
sudo gedit ubuntu/boot/grub/menu.lst
```

Change all "root (hd1,5)" in the ubuntu item to "root (hd2,5)" 

Reboot with the internal drive first in the boot order.  

You said that you cannot choose the boot order for the external drives. If for whatever reason you bios have decided that the boot order is hda,sda, sdb, the above might work


2)  A quick way to restore the Windows MBR. Boot from the live CD, open a terminal and type

```
sudo apt-get install ms-sys

sudo ms-sys -m /dev/hda
```


3)  Follow Pumalite's advice. Getting Supergrub ([Hermanzone info]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")) is always a good idea. It can restore  the Windows  MBR, and it might also be able to boot Ubuntu.

---

### Post by SimonFitz on 2007-11-25
I'm happy to keep trying any suggestions!

Option (2) - ran this, but upon boot I now get the message "Grub Hard Disk Error". Herman's page on this ([http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_hard_disk_error](http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_hard_disk_error)) has links to other threads here but I can't see what can help me there. Does this new error message shed any new light?

Option (3) - I have a temperamental cd writer so I wasn't holding out much hope of being able to burn a copy of Super Grub Disk. It seems that Ubuntu is better than XP (again!) as the LiveCD (in my dvd-rom drive) allowed me to burn the iso. However, the couple of options I have run so far haven't worked but I will keep working through them. 

Fixing the Windows MBR said it succeeded but reboot = grub hard disk error.

Trying the booting Windows option ran these commands
```
grub>  rootnoverify (hd0,1)  
grub>  makeactive
grub>  chainloader +1
grub>  boot_
```
but returned "Grub hard disk error". These were the commands I would have tried as per Herman's site if I could get to a Grub menu.

I will try option (1) if I don't get anywhere with SGD.

Thanks

#EDIT 1#
Tried the "Boot Windows" option ... the screen briefly displayed text something along the lines of XP preinstallation environment, displayed the usual XP booting logo for a couple of a seconds but then crushed my hopes with a BSOD ("The Session manager initialization system process terminated unexpectedly"). I'll google that separately.

I then tried the Boot Linux option just in case, but unsurprisingly it returned grub error 15 - file not found. I expected that because SGD only shows the internal disk (hd0) but you never know!

#EDIT 2 --- NEW PROBLEM!#
I've now managed to make things even worse - I can no longer access my internal drive via the LiveCD. Trying to mount hda through the file browser errors out as do via the terminal:
```

ubuntu@ubuntu:~$ sudo mount /dev/hda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or s

ubuntu@ubuntu:~$ dmesg | tail
[ 1920.121589] NTFS-fs warning (device hda2): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[ 1920.122144] NTFS-fs warning (device hda2): is_boot_sector_ntfs(): Invalid boot sector checksum.
[ 1920.122152] NTFS-fs error (device hda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
[ 1920.122156] NTFS-fs error (device hda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[ 1920.122161] NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS volume.

```

Same errors after
```

ubuntu@ubuntu:~$ sudo ms-sys -m /dev/hda
Windows 2000/XP/2003 master boot record successfully written to /dev/hda

```

What on earth have I done and what can I do now?

---

### Post by meierfra on 2007-11-25
> sudo mount /dev/hda2 /mnt

Try ```
sudo  mount  -nfts   /dev/hda2 /mnt
 Edit:  this should be:
sudo  mount  -t ntfs   /dev/hda2 /mnt

```
instead.

```
ubuntu@ubuntu:~$ sudo ms-sys -m /dev/hda
Windows 2000/XP/2003 master boot record successfully written to /dev/hda
```

That is not an error message. It is a success message.

> Option (2) - ran this, but upon boot I now get the message "Grub Hard Disk Error".

That is strange. Grub should not be involved any more.  Did you boot from the internal drive? You might repeat Option (2) with the USB drives unplugged.


Forget about Option (1) for now. Instead just unplug your second external drive. Then  try to boot Ubuntu with Supergrub, (Supergrub should see your external drive)

---

### Post by SimonFitz on 2007-11-25
> **meierfra said:**
> Try ```
sudo  mount  -nfts   /dev/hda2 /mnt
```
instead.
The terminal doesn't give any feedback after using the "-nfts" options; it just goes to a new line. Is that correct? In an attempt to understand, I've had a look through the manual for the mount command and I think the options added are for "mount without writing in /etc/mtab", no system call, indicating a file system type and "tolerate sloppy mount options". I did mistype the command first time (yes, copy & paste is my friend!) by switching the "t" and the "f" but it said "unknown file system type fs". However, /mnt is empty in Nautilus...

I did some googling about the NTFS errors displayed in my second edit and found a suggestion to use "sudo mount -o errors=recover /dev/hda2 /mnt" (in [http://forum.linux-ntfs.org/viewtopic.php?p=594#594](http://forum.linux-ntfs.org/viewtopic.php?p=594#594)) - this displayed the files on my internal drive, but read only. That post indicated that should repair the boot sector using the backup boot sector, but when I unmounted /mnt and then tried "sudo mount /dev/hda2 /mnt" again the same errors as before came up.

> **meierfra said:**
> 
```
ubuntu@ubuntu:~$ sudo ms-sys -m /dev/hda
Windows 2000/XP/2003 master boot record successfully written to /dev/hda
```

That is not an error message. It is a success message.
Sorry, should have been clearer in my post. I realise this was a success message, only I had hoped it would reverse whatever caused the problem. Rebooting straight afterwards produced the "grub hard disk error" message.

> **meierfra said:**
> 
That is strange. Grub should not be involved any more.  Did you boot from the internal drive? You might repeat Option (2) with the USB drives unplugged.

Forget about Option (1) for now. Instead just unplug your second external drive. Then  try to boot Ubuntu with Supergrub, (Supergrub should see your external drive)

My 'second' external usb drive (sdb aka F: ) has been unplugged since yesterday. The external usb drive that has my Ubuntu boot (sda6) and home (sda5) partitions is not seen by Supergrub.

I will unplug this drive (sda) and boot, and if that doesn't work then I will use the "ms-sys" command again through the livecd - option (2).

Thanks

Simon

---

### Post by meierfra on 2007-11-25
> sudo  mount  -nfts   /dev/hda2 /mnt

My bad, it should be 

```
sudo  mount  -t ntfs   /dev/hda2 /mnt
```

(I had two typos:  -t was missing and it needs to be "ntfs" not "nfts"

---

### Post by meierfra on 2007-11-25
Actually to get read and write access you need:

```
sudo  mount  -t ntfs-3g   /dev/hda2 /mnt
```

---

### Post by SimonFitz on 2007-11-25
> **meierfra said:**
> Actually to get read and write access you need:

```
sudo  mount  -t ntfs-3g   /dev/hda2 /mnt
```

After installing ntfs-config ...
```

ubuntu@ubuntu:~$ sudo  mount  -t ntfs-3g   /dev/hda2 /mnt
Unexpected clusters per mft record (-127).
Failed to startup volume: Invalid argument
Failed to mount '/dev/hda2': Invalid argument
The device '/dev/hda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

Um? Not going to try anything else yet ...

Prior to the above, I tried to boot with no external drive(s) attached. Having just "hdd-0" (or -1, 2 or 3) selected as the first boot device with all others disabled in the Bios produced the familiar "grub hard disk error" message. 

Next using Supergrub to choose the Windows boot partition got me a bit further, but what happened was as described in my "Edit 1" post earlier ... there was a message "NTDetect Checking Hardware", then the screen displayed a loading the "Windows XP Preinstallation Environment", then the XP logo for a short time before blue screening with a fatal system error of "stop c000021a". I haven't installed any Microsoft hotfixes/updates etc for ages which other websites indicate is the usual cause for this stop message. I don't know if it is relevant, but this route using Supergrub bypasses my Boot.Ini file.

Haven't rerun ms-sys yet as the above might shed light on things.

Cheers

---

