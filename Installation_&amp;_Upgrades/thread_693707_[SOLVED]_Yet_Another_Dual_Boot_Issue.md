---
title: "[SOLVED] Yet Another Dual Boot Issue"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by cptInsane0 on 2008-02-11
I tried to solve this issue without resorting to starting a thread, but I am out of ideas.  The other day, I decided to reinstall Gutsy due to the upgrade messing up some of my stuff. I have four hard drives in my computer: (2) 160 Gig SATA2 drives, a 320Gb IDE Drive, and a 200GB IDE Drive.

Both Ubuntu and WIndows reside on the first 160 GB drive.  During the installation, I let grub be installed on HD0, which is where it should be.  However, I can no longer get into windows.  I just get NTLDR is missing.

I figured that maybe grub just doesn't know where windows is, which is still possible. I had to change Ubuntu from (HD2,1) to (HD0,1), since the bios lists IDE drives first, then SATA.  However, it is set to boot from the SATA, which technically makes it HD0.  Following that same logic, Windows should be on (HD0,0).  When I change that in the grub menu, it gives me the NTLDR error.  If I leave it at HD2,0, I get the same thing.

I figured that maybe I messed up the MBR or something, so I popped in a windows disk, and started the recovery console.  I ran fixboot C: and fixmbr. The problem is, It decided that the IDE drive was C, and now the partition information on the 320 gig with everything I own is messed up.  Good times.  I will post my menu.lst and anything else that's needed, but I am in a bind, and would appreciate any help that is offered.

Thanks in advance.

---

### Post by mikewhatever on 2008-02-11
Please post the outputs of the following:
sudo fdisk -l
cat /boot/grub/device.map
cat /boot/grub/menu.lst

---

### Post by cptInsane0 on 2008-02-11
Fdisk:

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69737369

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *      116388      126889    84344761   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hda2          105915      222310   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hda3               1           1           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/hda4               1      213826  1717556736    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hda4: 1758.7 GB, 1758778097664 bytes
255 heads, 63 sectors/track, 213825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69737369

     Device Boot      Start         End      Blocks   Id  System
/dev/hda4p1   *      116388      126889    84344761   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hda4p2          105915      222310   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hda4p3               1           1           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/hda4p4               1      213826  1717556736    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d8accf4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10543    84686616    7  HPFS/NTFS
/dev/sda2           10544       19088    68637712+  83  Linux
/dev/sda3           19089       19457     2963992+   5  Extended
/dev/sda5           19089       19457     2963961   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000af1d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    b  W95 FAT32

---

### Post by cptInsane0 on 2008-02-11
Device.map:

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/hda
(hd3)   /dev/hdb
(hd4)   /dev/sdc



Menu.lst:

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=732f3e0c-c669-4794-a1d6-3091ad495e6a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd2,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=732f3e0c-c669-4794-a1d6-3091ad495e6a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd2,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=732f3e0c-c669-4794-a1d6-3091ad495e6a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd2,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

---

### Post by mikewhatever on 2008-02-11
I doubt you need chainloading at all, since /dev/sda is seen as hd0, the first HDD. Try --> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by cptInsane0 on 2008-02-11
No luck. It just goes to a blank screen when I do that.

---

### Post by cptInsane0 on 2008-02-11
I am at my wits end. Supergrub won't even do it. It won't boot me into ubuntu either though, I am guessing it is an issue with the size of my drive and the way it's partitioned. Does anyone have any suggestions? I am about to give up, delete ubuntu, and never let it near my pc again, which is sad, since i use it on a daily basis at my job and like it for the most part.

---

### Post by Shazaam on 2008-02-11
Ok, you have Ubuntu and Windows on one 160gig drive, a 320gig and a 200gig drive (2 storage drives?), and another 160gig drive.
What's this-- Disk /dev/hda4: 1758.7 GB?
What's on the other 160gig drive (sdb)?

Try with just the basics. Disconnect all of the hard drives except the Ubuntu/Windows one. In the bios make it the first boot drive. Then sort out the boot problems with it (grub, fstab, menu.lst) using either the Ubuntu livecd or the SuperGrubDisk.

---

### Post by cptInsane0 on 2008-02-11
All three of the other drives are storage. None are full, but I just have things very organized. The two 160 gigs used to be a RAID array a while back. Unhooking all the other drives gives similar results. I can still boot into ubuntu just fine, but now when I try to boot windows it just says disk read error, which makes no sense whatsoever.


If I use the super grub disk with only the main drive hooked up, I can get into windows.  Wiskey...Tango...Foxtrot?

---

### Post by Shazaam on 2008-02-11
Wiskey...Tango...Foxtrot? Indeed.:)
With just the one drive hooked up have you tried to reinstall grub?
As an aside, make sure that the only drive that has it's jumpers set as MASTER is the Ubuntu/Windows drive. Set the others as SLAVE if you are using them as storage drives.

---

### Post by cptInsane0 on 2008-02-11
Haven't done the grub install yet, although my coworker suggested it to me already. I am basking in the glow of working windows, as I do a lot more in windows than linux.  Also, as far jumpers go, I have the two IDE's on one cable, one as master and one as slave. SATA drives don't have to be ID'd.

---

### Post by ScottyPDX on 2008-02-11
Hello,

I JUST went through this EXACT same thing with my dual boot. Vista Recovery disk won't work until you use TESTDISK (in Ubuntu) Make sure you have the latest one (from Synaptic) then go to a terminal. Make sure you have 25 lines (full screen) then type:

   sudo testdisk

You will get a menu, choose ANALYZE, then highlight the disk to analyze.

It will analyze the entire disk and give a readout. Highlight the NTFS disk, then enter.

Next, choose the next option down (I don't remember exactly what the option is), but choose REBUILD NT Boot Record, then LIST. You should see your files. Then WRITE changes, and QUIT, reboot with your Vista Recovery disk. This brought my Windows back.

Good Luck!

---

### Post by cptInsane0 on 2008-02-11
I don't use Vista. Also, I tried reinstalling grub, and it didn't make a difference.

---

### Post by cptInsane0 on 2008-02-11
Well, after disconnecting all the other drives, and running fixboot and fixmbr, I can now load into windows again. I know I need to reinstall grub to get back into ubuntu, but I have another pressing issue.  That 320 gig that fixboot messed up.  It was formatted in NTFS, and has about 220GB of stuff on it. Does anyone here know of recovery software that will just fix the partition table, instead of having to find a big enough drive to back it up to?

---

### Post by harold4 on 2008-02-11
The native disk checker in the XP recovery console.

Whoever got you that far... you should buy him lunch when you're farther north. ;)

---

### Post by cptInsane0 on 2008-02-11
Hehe, yeah. There are a lot of different sources offering help. I would go broke buying everyone lunch. I tried to reinstall grub again after I got windows working, and it broke again, just giving me a disk read error. I redid fixboot and fixmbr and can now get into windows. I think I will save fixing grub for another day. My concern now is to get my information safely recovered. Thank you everyone for your help so far.

---

### Post by harold4 on 2008-02-12
When you get to grub, edit the windows option and see where it's pointing.  e.g. hd(x,y)

---

### Post by harold4 on 2008-02-13
Let the searchers know what you did and mark the thread solved.

Forgot the name of the CD you used.

---

### Post by cptInsane0 on 2008-02-13
It isn't completely solved, although most people following this would be ok if they did.  I ended up unplugging all my extra drives(DO THIS), and putting in my xp disk.  Then I went into the recovery console, typed fixboot C:, then fixmbr. This fixed the windows issue. Of course, this kills grub.  At this point, anyone else could just reinstall grub. I did that and it broke again, so I fixed it again and just made a grub boot floppy for when I need ubuntu.  Also, when I ran fixboot before I unplugged my drives, it messed up my 320 gig by breaking the partition.  I used Active Partition Recovery 3.0 on a certain boot cd, and it rebuilt everything in about 30 seconds.  Luckily it only took me like three days to discover this. So for the most part, problem solved.

---

### Post by Mark Phelps on 2008-02-13
Like you, I have a multi-boot, multi-disk system.  In my case, ubuntu is on an IDE drive, Windows is on a SATA drive.  I recently added another IDE drive and had to edit the menu.lst file to get Windows back.  I noticed that my windows entry is slightly different:

map (hd0) (hd2) 
map (hd2) (hd0) 
rootnoverify (hd2,0) 
savedefault 
chainloader +1

Like you, Windows is on HD 2, but unlike you, I'm using rootnoverity and setting it to point to (hd2,0), instead of (hd0,0).  Could it be that simple a difference?

---

