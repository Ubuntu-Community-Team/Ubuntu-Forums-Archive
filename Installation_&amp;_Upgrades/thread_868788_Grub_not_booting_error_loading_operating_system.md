---
title: "Grub not booting error loading operating system"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by jukingeo on 2008-07-24
Hello all, 

I was wondering if someone could help me with a situation I am having with Grub.

First a little background.  I had Ubuntu working fine on a dual boot setup with Windows XP.  Everything was fine with Grub and it did what it supposed to do.  However, I had a partitioning accident  and lost my Windows partition.  Needless to say I spent a good 6 hours or so loading everything back on to Windows.  BUT (there is always a BUT), Windows decided to replace Grub with a bootloader of it's own and of course it booted fine into Windows, but left Ubuntu in the dust.

Being that I had problems with my Ubuntu partition to begin with I decided to nix it and start over.  With reinstallation complete, I booted up the system and I get this error message:

Error:  Couldn't load operating system.

And it just sits there.

So I decided to try a "warm boot" from the boot menu instead.  I selected the first drive and Grub came up!   From here I can get into Ubuntu, but not Windows.

So I have two problems I need to fix:

1) Get rid of the error message on bootup
2) Fix the Windows bootup selection.

Any assistance would be much appreciated.

Thank You,

Geo

---

### Post by Pumalite on 2008-07-24
I would check the partition table with rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
You can fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by jukingeo on 2008-07-24
> **Pumalite said:**
> I would check the partition table with rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
You can fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Hello,

Thank you for responding, but do you have a solution that doesn't involve "wasting" a disc?

Thank You,

Geo

---

### Post by dstew on 2008-07-24
The error message "Error: Couldn't load operating system" comes from the Vista boot loader. You probably messed up the Vista bootloader configuration when you re-installed Ubuntu. If you want to use the Vista boot loader to dual-boot Vista and Ubuntu, you will have to reconfigure it.

I am not sure what you mean by a "warm boot". Is that a BIOS program, or possibly a part of the Vista boot loader? It does not sound like part of grub.

I would recommend installing grub to dual boot Vista and Ubuntu. You can do this using the Ubuntu live CD. Open a terminal and enter```
sudo grub
```That should get you the grub shell, with the **grub>** prompt. At the grub prompt, enter```
find /boot/grub/stage2
```That should get you the name of the grub root partition in grub-speak, say (hd0,0). Whatever it returns, use as the argument for a root statement:```
root (hd0,0)
```Then, install the boot loader into the MBR of the first hard disk, and quit:```
setup (hd0)
quit
```Hopefully you will get the grub menu at boot time. Let us know if Vista will boot from the grub menu item or not. If not, we should be able to configure grub to boot Vista.

---

### Post by jukingeo on 2008-07-24
Hello Dstew,

I am on Windows XP and not Vista.  However, I did as you instructed and it didn't work.  I still have both problems.  On a cold boot (which means when you first turn on the machine)  I still get the "Cannot load operating system" error.  On a warm boot (you are booting to someplace with the machine already turned on...in this case I am instructing the computer to pull up the boot menu), going into the boot menu if I pick Windows, it still isn't loading it up.

Geo

---

### Post by Pumalite on 2008-07-24
Post your menu.lst

---

### Post by dstew on 2008-07-25
Are you sure you have your BIOS set to boot the correct disk? You might have to tell it to boot from the hard disk where you installed grub. Did you get any error messages when you installed grub?

---

### Post by jukingeo on 2008-07-25
Update:

Frustrated with this problem, last night I wiped both operating systems from my machine COMPLETELY.

My main drive is an 80gig IDE and the Linux drive is a 500gig SATA.

This is what I did:

1) Deleted both drives and deleted all partitions on the Sata drive so Windows will not even see that it exists.

2) Installed Windows and tested it that it boots fine from start up.

3) Reconfigure the Sata drive and installed Ubuntu

4) Told Grub to install on the first disk MBR.

Now when I tested the installation I still get the confounded "Error: Couldn't Load Operating System" message.

However, if I go into the F12 boot menu I CAN now get into both Windows and Linux without a problem.   So one issue was taken care of.

So being that Windows booted fine prior to loading up Ubuntu and I have the same problem...AGAIN, I am assuming that Grub is causing the problem.

The problem isn't with BIOS either as I did check it and it is correctly set up.  Also the fact that Windows loaded in fine prior to the Ubuntu installation is further proof that the BIOS is OK.

So something is wrong when the machine is first turned on.  Also selecting "Normal" from the boot menu will also yeild the same error message.  So something must be very wrong with the first part of the boot up procedure that tells the system which drive to boot up (so I can see why many are thinking that Bios is the problem).  But it is software not firmware because the problem isn't happening with Windows alone.  Also because I loaded everything up separately, the Windows bootloader was out of the question this time around.

So at this point in time if I delete everything and start over, it will probably happen again.  So I think I have to get right in there on the MBR and find the problem and fix it, or perhaps I should use a different bootloader than Grub.

Any ideas or advice?

Thank You,

Geo

---

### Post by dstew on 2008-07-25
Did you try to boot Windows after you put the SATA drive back, but before you installed Ubuntu? When you go to F12 and get a boot menu, does it give you choices of disks or partitions?

---

### Post by jukingeo on 2008-07-25
> **dstew said:**
> Did you try to boot Windows after you put the SATA drive back, but before you installed Ubuntu? When you go to F12 and get a boot menu, does it give you choices of disks or partitions?

I actually never removed the Sata drive.  I effectively 'took it out of the picture' by deleting all the partitions so this way Windows couldn't see if the drive was there.  If it can't see the drive, it can't find anything that could be interpreted as another operating system (such as the presence of another bootable partition).

I then installed Windows and tested it.  It booted fine like it normally would.

Only then did I reset up the SATA drive and install 64Studio and Grub.

Yes, F12 does work and I get these choices:

1) Normal  (Yeilds the NOS error)
2) SATA    (Also yeilds the error)
3) Primary Master Hard Drive (This will give me the grub menu and I can get into both Windows and 64Studio from here).
4) IDE Primary Drive C:  (This is the one that SHOULD work, but I get the error here too)
5) Floppy Drive
6) USB port
7) IDE CD-Rom

The boot up in bios allows me to point to the IDE Primary Drive C:, the floppy, the USB port, or IDE CD-Rom.   It will not allow me to set boot to the Sata drive or the Primary Master Hard Drive.

I believe Grub moved something from the C: drive to another place on the Primary Master Hard Drive and now my Bios cannot see this "something" to boot up to.

I am wondering at this point if it is possible to examine the MBR and see if it is where it should be in the first place.  Is this something that can be edited or configured?

Finally, my patients is growing thin with this problem and I am wondering if there is perhaps another bootloader that I can use that is FULLY configurable.  But then the question comes to mind with what to do with Grub?  Could this be deleted?

On my first Ubuntu disk I didn't have this problem when setting it up.

So I don't know what is going on.

Edit: This is my disk listing in case anyone wants to take a peek

geo@64studio:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         851     6835626   83  Linux
/dev/sda2             852       60801   481548375    5  Extended
/dev/sda5             852        1181     2650693+  82  Linux swap / Solaris
/dev/sda6            1182       13339    97659103+  83  Linux
/dev/sda7           13340       31575   146480638+  83  Linux
/dev/sda8           31576       46164   117186111   83  Linux
/dev/sda9           46165       60801   117571671    b  W95 FAT32

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7333    58902291    7  HPFS/NTFS
/dev/hda2            7334        9726    19221772+   b  W95 FAT32
geo@64studio:~$


According to this everything LOOKS right.

Just to make things easier hda2, sda7 through 9 are all data storage.  hda1 is my Windows, and sda 1 through 6 (only 4 partitions though) are Linux. Sda2 starts the Extended partition which encompases 5 through 9.  Sda1 is the Linux root/boot partition. Sda6 is the /home partition and where my Linux programs are stored.

This is my grub menu.lst:

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
timeout 	10

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
# kopt=root=/dev/sda1 ro vga=791 splash=silent

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		64studio, kernel 2.6.21-1-multimedia-486
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-486 root=/dev/sda1 ro vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.21-1-multimedia-486
savedefault

title		64studio, kernel 2.6.21-1-multimedia-486 (single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-486 root=/dev/sda1 ro vga=791 splash=silent single
initrd		/boot/initrd.img-2.6.21-1-multimedia-486
savedefault

title		64studio, kernel memtest86
root		(hd1,0)
kernel		/boot/memtest86.bin

title		64studio, kernel memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


This is my device map to help with drive correspondence

(hd0)	/dev/hda
(hd1)	/dev/sda


Now my personal experience is minimal with Ubuntu/Linux, but it does look to be that everthing is in place.  Once I can GET to Grub, it works!  I just can't boot to it on start up and that is my final issue.

At any rate I did look into another Boot Loader such as Lilo and it looks promising, but the directions are not the easiest to follow.

I am REALLY going to need assistance from a boot loader expert on this one because I can't move forward until this problem is fixed.


Geo

---

### Post by jukingeo on 2008-07-25
> **Pumalite said:**
> Post your menu.lst

Here is my menu.lst:

# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
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
timeout 	10

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
# kopt=root=/dev/sda1 ro vga=791 splash=silent

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		64studio, kernel 2.6.21-1-multimedia-486
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-486 root=/dev/sda1 ro vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.21-1-multimedia-486
savedefault

title		64studio, kernel 2.6.21-1-multimedia-486 (single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-486 root=/dev/sda1 ro vga=791 splash=silent single
initrd		/boot/initrd.img-2.6.21-1-multimedia-486
savedefault

title		64studio, kernel memtest86
root		(hd1,0)
kernel		/boot/memtest86.bin

title		64studio, kernel memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1



Since I did a full reinstall of both operating systems, I CAN get into them both from the F12 boot menu, but Grub will NOT load up on machine start up.  It always yeilds an "Error: Cannot Load Operating System" message.

I did look over this menu.lst carefully and I didn't see anything in regards to where Grub is set up to appear upon bootup.

According to my BIOS it SHOULD appear on the IDE Master Drive C:, but it instead appears on my Primary Master Drive.  The F12 menu list has these listed separately and, yes, if I select IDE Master Drive C (or Normal boot) I will get the infamous error message above.

So it would see though from the error message, Grub moved something that it shouldn't have.  I am wondering if that is something that can be fixed or if not, if it is possible to delete Grub and use a different boot loader.

Thanx,
Geo

---

### Post by dstew on 2008-07-25
One thought about your BIOS choices. It is a little strange that your BIOS gives you the choice of a C: drive. That is the name of a partition, in DOS/Windows format. Unless you specifically installed grub to that partition, there would not be a boot loader there. Usually, the default is to install grub to the MBR of the boot disk, which is not a part of any partition.

There is some confusion about this, because many Windows users have only one partition, and they are used to thinking of C: as a disk. But it is really a partition. And, some BIOSes have the capacity to boot a partition, so it makes sense.

Maybe you could figure out which partition is C: and re-install grub there. It might them make your BIOS happy, even though it is a bit non-standard. I would think you should be able to tell your BIOS to boot the "Primary Master Hard Drive", which probably means the MBR of one of the drives, by some part of its menu. Since it works if you pick this from the F12 boot choices, you know that grub is installed correctly somewhere, probably the MBR of one of the disks. Look for a BIOS menu choice that lets you designate the Primary Master drive, and see if you can change it.

---

### Post by Pumalite on 2008-07-25
You have a mix of SATA and IDE. Search in the Forum for Dualbooting Two Hard Drives. BTW, Super Grub is a great disk to have around and you'll never 'waste' a CD with it.

---

### Post by jukingeo on 2008-07-25
> **dstew said:**
> One thought about your BIOS choices. It is a little strange that your BIOS gives you the choice of a C: drive. That is the name of a partition, in DOS/Windows format. Unless you specifically installed grub to that partition, there would not be a boot loader there. Usually, the default is to install grub to the MBR of the boot disk, which is not a part of any partition.

Well, I will say that Dell created the Bios and for the most part (and up until recently) they only been using Windows.  So it could very be they set up the Bios to look for a C: partition to boot from.

> Maybe you could figure out which partition is C: and re-install grub there. It might them make your BIOS happy, even though it is a bit non-standard.

Ahhh, now that is the weird thing.  On my IDE primary hard drive there are only two partitions that I know about.  One is set (by me) as a FAT32 for storage, so there is only ONE partition left.  Something is wrong with boot table, that is what I think.

>  I would think you should be able to tell your BIOS to boot the "Primary Master Hard Drive",

Perhaps, that would make sense, but keep in mind, this is a Dell machine, so they are doing to do what THEY want with the Bios, not what is considered standard.  According to my Bios, it will ONLY boot from a drive that is designated as IDE Primary C:.  I will not boot from secondary drives.

> . Since it works if you pick this from the F12 boot choices, you know that grub is installed correctly somewhere, probably the MBR of one of the disks. Look for a BIOS menu choice that lets you designate the Primary Master drive, and see if you can change it.

I don't think it can be changed.  I looked several times.  It is also true that I am not 100% sure what the master primary drive is.  I am guessing that it is the C: drive, but I could be wrong about that.  For some reason on the boot menu they are separting the C: designation from the master primary drive.  The C designation IS in the boot up list for primary boot up device, however, if I click on this in the Boot Menu, I get the error message.  So it would seem that some how Grub moved the MBR away from the C: designated drive.  And because I can't re-assign the boot up through Bios...I'm stuck.

Now the really really weird thing is that with straight Ubuntu, I didn't have this problem. Grub worked.

I will say that Grub does look different from when I went to Ubuntu to Ubuntu Studio and now I am on 64Studio.

Anyway I want to try a trick.  Is there a way I can turn off Grub, I want to see if my machine will boot back directly to Windows.

EDIT:

Ok, I went back into Bios and I confirmed that in the boot order for the drives the Choices are IDE Hard Disk C:, Floppy, IDE CD-Rom, and USB.  The Hard disk designation CANNOT be changed.  Over in the F12 menu there is the IDE Hard Disk C label as well and if I click on that I get the error.  More then likely on a normal boot, this is the drive the Bios is pointing to.   So if I pick Primary Master Drive (which by the way isn't giving a clear indication if this is the IDE drive or the SATA drive) it works.  

So my guess is if Grub is working on THIS Primary Master Drive, it moved the MBR to this drive as well.  So it would make sense if the MBR and Grub were moved back to the C: designated drive, my machine should boot normally.

So this all is confirming Grub did something it shouldn't have.  However, the thing is this...where is Grub?  

Thanx,

Geo

---

### Post by dstew on 2008-07-26
Without doing any experiments, it seems your BIOS will only boot the IDE drive, unless you use the F12 boot menu. It is calling the IDE drive "C:" even though this is not really correct, since C: really is a name for a Windows or DOS partition, and not a proper disk name.

The MBR (Master Boot Record) is a region of a hard disk that is set aside for a boot loader and a disk partition table. It is part of the first track on the disk, and not part of any partition. An MBR may or may not have a boot loader in it, but it will have a partition table, if there are any file systems on the disk.

> However, the thing is this...where is Grub? There is a way to see if grub is in the MBR of a particular disk. You can use the program lde (Linux Disk Editor) to get a data dump of sector 0 on a drive. If grub is there, you will see the brief messages it contains in the ASCII translation of the data dump for that sector. Here is the data dump of sector 0 (the Master Boot Record) on my first hard disk:```
0x00000000  EB 48 90 D0 BC 00 7C FB : 50 07 50 1F FC BE 1B 7C  .H....|.P.P....|
0x00000010  BF 1B 06 50 57 B9 E5 01 : F3 A4 CB BD BE 07 B1 04  ...PW...........
0x00000020  38 6E 00 7C 09 75 13 83 : C5 10 E2 F4 CD 18 8B F5  8n.|.u..........
0x00000030  83 C6 10 49 74 19 38 2C : 74 F6 A0 B5 07 B4 03 02  ...It.8,t.......
0x00000040  FF 00 00 20 01 00 00 00 : 00 02 FA 90 90 F6 C2 80  ... ............
0x00000050  75 02 B2 80 EA 59 7C 00 : 00 31 C0 8E D8 8E D0 BC  u....Y|..1......
0x00000060  00 20 FB A0 40 7C 3C FF : 74 02 88 C2 52 BE 7F 7D  . ..@|<.t...R..}
0x00000070  E8 34 01 F6 C2 80 74 54 : B4 41 BB AA 55 CD 13 5A  .4....tT.A..U..Z
0x00000080  52 72 49 81 FB 55 AA 75 : 43 A0 41 7C 84 C0 75 05  RrI..U.uC.A|..u.
0x00000090  83 E1 01 74 37 66 8B 4C : 10 BE 05 7C C6 44 FF 01  ...t7f.L...|.D..
0x000000A0  66 8B 1E 44 7C C7 04 10 : 00 C7 44 02 01 00 66 89  f..D|.....D...f.
0x000000B0  5C 08 C7 44 06 00 70 66 : 31 C0 89 44 04 66 89 44  \..D..pf1..D.f.D
0x000000C0  0C B4 42 CD 13 72 05 BB : 00 70 EB 7D B4 08 CD 13  ..B..r...p.}....
0x000000D0  73 0A F6 C2 80 0F 84 EA : 00 E9 8D 00 BE 05 7C C6  s.............|.
0x000000E0  44 FF 00 66 31 C0 88 F0 : 40 66 89 44 04 31 D2 88  D..f1...@f.D.1..
0x000000F0  CA C1 E2 02 88 E8 88 F4 : 40 89 44 08 31 C0 88 D0  ........@.D.1...
0x00000100  C0 E8 02 66 89 04 66 A1 : 44 7C 66 31 D2 66 F7 34  ...f..f.D|f1.f.4
0x00000110  88 54 0A 66 31 D2 66 F7 : 74 04 88 54 0B 89 44 0C  .T.f1.f.t..T..D.
0x00000120  3B 44 08 7D 3C 8A 54 0D : C0 E2 06 8A 4C 0A FE C1  ;D.}<.T.....L...
0x00000130  08 D1 8A 6C 0C 5A 8A 74 : 0B BB 00 70 8E C3 31 DB  ...l.Z.t...p..1.
0x00000140  B8 01 02 CD 13 72 2A 8C : C3 8E 06 48 7C 60 1E B9  .....r*....H|`..
0x00000150  00 01 8E DB 31 F6 31 FF : FC F3 A5 1F 61 FF 26 42  ....1.1.....a.&B
0x00000160  7C BE 85 7D E8 40 00 EB : 0E BE 8A 7D E8 38 00 EB  |..}.@.....}.8..
0x00000170  06 BE 94 7D E8 30 00 BE : 99 7D E8 2A 00 EB FE 47  ...}.0...}.*...G
0x00000180  52 55 42 20 00 47 65 6F : 6D 00 48 61 72 64 20 44  RUB .Geom.Hard D
0x00000190  69 73 6B 00 52 65 61 64 : 00 20 45 72 72 6F 72 00  isk.Read. Error.
0x000001A0  BB 01 00 B4 0E CD 10 AC : 3C 00 75 F4 C3 00 00 00  ........<.u.....
0x000001B0  00 00 00 00 00 00 00 00 : 76 7A 07 00 00 00 80 01  ........vz......
0x000001C0  01 00 07 FE FF FF 3F 00 : 00 00 AF C7 45 04 00 FE  ......?.....E...
0x000001D0  FF FF 83 FE FF FF EE C7 : 45 04 0C F1 02 00 00 FE  ........E.......
0x000001E0  FF FF 83 FE FF FF FA B8 : 48 04 C0 14 2A 01 00 FE  ........H...*...
0x000001F0  FF FF 05 FE FF FF BA CD : 72 05 C4 5A DD 03 55 AA  ........r..Z..U.
0x00000200  52 56 BE 03 21 E8 2A 01 : 5E BF F8 21 66 8B 2D 83  RV..!.*.^..!f.-.
0x00000210  7D 04 00 0F 84 CA 00 80 : 7C FF 00 74 3E 66 8B 1D  }.......|..t>f..
0x00000220  66 31 C0 B0 7F 39 45 04 : 7F 03 8B 45 04 29 45 04  f1...9E....E.)E.
0x00000230  66 01 05 C7 04 10 00 89 : 44 02 66 89 5C 08 C7 44  f.......D.f.\..D
0x00000240  06 00 70 50 66 31 C0 89 : 44 04 66 89 44 0C B4 42  ..pPf1..D.f.D..B
0x00000250  CD 13 0F 82 9F 00 BB 00 : 70 EB 56 66 8B 05 66 31  ........p.Vf..f1
0x00000260  D2 66 F7 34 88 54 0A 66 : 31 D2 66 F7 74 04 88 54  .f.4.T.f1.f.t..T
0x00000270  0B 89 44 0C 3B 44 08 7D : 74 8B 04 2A 44 0A 39 45  ..D.;D.}t..*D.9E
0x00000280  04 7F 03 8B 45 04 29 45 : 04 66 01 05 8A 54 0D C0  ....E.)E.f...T..
0x00000290  E2 06 8A 4C 0A FE C1 08 : D1 8A 6C 0C 5A 52 8A 74  ...L......l.ZR.t
0x000002A0  0B 50 BB 00 70 8E C3 31 : DB B4 02 CD 13 72 46 8C  .P..p..1.....rF.
0x000002B0  C3 8E 45 06 58 C1 E0 05 : 01 45 06 60 1E C1 E0 04  ..E.X....E.`....
0x000002C0  89 C1 31 FF 31 F6 8E DB : FC F3 A4 1F BE 14 21 E8  ..1.1.........!.
0x000002D0  60 00 61 83 7D 04 00 0F : 85 3C FF 83 EF 08 E9 2E  `.a.}....<......
0x000002E0  FF BE 16 21 E8 4B 00 5A : EA 00 22 00 00 BE 19 21  ...!.K.Z.."....!
0x000002F0  E8 3F 00 EB 06 BE 1E 21 : E8 37 00 BE 23 21 E8 31  .?.....!.7..#!.1
0x00000300  00 EB FE 4C 6F 61 64 69 : 6E 67 20 73 74 61 67 65  ...Loading stage
0x00000310  31 2E 35 00 2E 00 0D 0A : 00 47 65 6F 6D 00 52 65  1.5......Geom.Re
0x00000320  61 64 00 20 45 72 72 6F : 72 00 BB 01 00 B4 0E CD  ad. Error.......
0x00000330  10 46 8A 04 3C 00 75 F2 : C3 00 00 00 00 00 00 00  .F..<.u.........
0x00000340  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x00000350  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x00000360  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x00000370  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x00000380  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x00000390  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x000003A0  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x000003B0  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x000003C0  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x000003D0  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x000003E0  00 00 00 00 00 00 00 00 : 00 00 00 00 00 00 00 00  ................
0x000003F0  00 00 00 00 00 00 00 00 : 02 00 00 00 0F 00 20 02  .............. .

```You can see the "Loading stage 1.5" message in the ASCII (text translation) column, which shows that there is a grub boot loader there. You could do this to figure out where your grub went. You would need to boot a Live CD, install lde using Synaptic, and in a terminal issue the command```
sudo lde -b 0 /dev/sda | more
```This assumes your disks are named sda, sdb etc. If they are named hda etc, use those names. You can look at a raw data dump of the MBR of each disk this way.

This is just my experimental brain at work. More directly, you should just re-install grub to the IDE drive. [Here]("http://ubuntuforums.org/showthread.php?t=224351") are instructions on doing that.

---

### Post by jukingeo on 2008-07-26
> **Pumalite said:**
> You have a mix of SATA and IDE. Search in the Forum for Dualbooting Two Hard Drives. BTW, Super Grub is a great disk to have around and you'll never 'waste' a CD with it.

Guess what?  I got the best of both worlds.  I found out that the Super Grub installations has USB and Floppy versions as well.  I very rarely use my floppy drive, so I downloaded the Super Grub .iso and downloaded it to a Floppy.

Now here is something else I found out this afternoon. The Grub bootloader on the 64Studio installation WILL NOT WORK, even booting from a floppy, it STILL manipulates the MBR on the Windows drive.  In fact this afternoon it blew out my Windows so bad, I could use the repair option on the Windows installation disk, I had to redo Windows ALL OVER again.

Now I have a question for you about Super Grub before I use it.

1) Will it stay AWAY from my Windows MBR?
2) I don't care if I need a floppy to boot up 64Studio or Ubuntu for that matter.  I just want any bootloader I use to stay away from the Windows MBR.

I don't know what it is, but for some reason my machine wants to see the Windows MBR pointing to the C: drive.  My computer's Bios LOOKS for the C: drive.

Again, I didn't have this problem with the standard Ubuntu installation.  It's Grub worked fine.

So I am willing to try Super Grub or another bootloader altogether (I am thinking Lilo here), but I want it to stay away from the Windows drive and it's MBR...period.

So with that smoke cleared out of the way...can Super Grub do this?

Thanx,

Geo

---

### Post by jukingeo on 2008-07-26
> **dstew said:**
> Without doing any experiments, it seems your BIOS will only boot the IDE drive, unless you use the F12 boot menu. It is calling the IDE drive "C:" even though this is not really correct, since C: really is a name for a Windows or DOS partition, and not a proper disk name.

The MBR (Master Boot Record) is a region of a hard disk that is set aside for a boot loader and a disk partition table. It is part of the first track on the disk, and not part of any partition. An MBR may or may not have a boot loader in it, but it will have a partition table, if there are any file systems on the disk. 


Hello dstew,

I had another disaster this afternoon when I attempted to create 64Studio with a boot off of a floppy.  I figured that when I installed it that when it came to part to install Grub, that I could tell it to set itself up on a floppy.  Then I could boot my machine from the floppy and from there make my choice.  

However, once again...EVEN with a floppy boot, Grub decided to alter the Windows MBR.  This time it was so bad that I had to delete the Windows partition (the repair option on the Windows installation disk wouldn't work).

At this point now I am fed up with Grub trying to mess around with the Windows hard drive and the MBR.

I did find out that the version of Grub isn't the same on the 64Studio install when compared to that of standard Ubuntu.  Ubuntu has a better version of Grub.  BUT the thing is with the 64Studio installation, you are pretty much forced to use IT's Grub.

I didn't want to try the CD-Rom or USB methods because if I can't do a boot from a Floppy without grub messing up the Windows MBR, then I am pretty sure the other installations will mess it up too.

So the only thing that I can think of (and it was also suggested to me by someone else), is now that I have Windows running again, is to disconnect the Windows IDE drive from my machine.  Thus an install of 64Studio on my SATA drive would "FORCE" Grub to either load itself on the SATA drive or set up to boot from let's say a floppy drive.  I figured once set up, Grub shouldn't touch the Windows drive anymore and I could reconnect it.

Now I am not sure what will happen to my system Bios if it sees the SATA drive and no IDE drive.  I would be hoping that it would see it as a bootable drive and as such make Grub happy.

However, I am not totally sure what will happen after I plug my IDE drive back in.  Would Grub try and take over the Windows hard drive again?

At any rate I am willing to explore other bootloading options.  I did find out that Super Grub can be set up from a floppy drive and I downloaded it and put it on a floppy, so I DO have Super Grub now.

The only requirement I would like to make at this point is that I want ANY bootloader I use NOT interfere with the Windows drive MBR.  It is working now and this is the last time I am reinstalling Windows.  If that means I have to boot 64Studio/Ubuntu or whatever other version of Linux I use, I don't care.  The bottom line is that I am sick of this particular version of Grub I been dealing with that constantly does what it wants to with the Windows MBR.

So that is my main criteria right now.  I don't want whatever choice of bootloader I end up using to mess with the Windows MBR.

Thank You,

Geo

---

### Post by red_team316 on 2008-07-27
GRUB is the best bootloader out there hands down. You will not find a better one out there(unless GRUB2 ever comes about)

Since it appears that you are mixing SATA and IDE drives, that could be part of the problem. I think I've seen somewhere that when you have a IDE plugged in, it tries to take the top spot.

What dstew posted about going into a grub shell and doing the root (hd0,0)/ setup (hd0) thing is exactly correct. The only problem appears to be that it may be hd1 that you need to set up(I come to this conclusion from looking at your menu.lst).

Other than that, once you have GRUB installed to the MBR of the correct drive, you need to make sure that your BIOS is set up to boot from that drive first. I know that it can get very confusing what drive is what if you start switching orders, but if you can get to the GRUB bootup menu, then you can edit the lines before you boot and that will definitely nail down whether it's looking at the wrong drive.

Take a look at the links in my sig. This is how I am booting several distros at the same time by keeping GRUB in the MBR and GRUB's data in it's own partition. Once you understand what he has posted, you should never have to reinstall any bootloader ever again until your drive fails.

---

### Post by jukingeo on 2008-07-27
> **red_team316 said:**
> GRUB is the best bootloader out there hands down. You will not find a better one out there(unless GRUB2 ever comes about)

Well, that may be true of the newer version, but the one that comes with 64Studio isn't winning any awards with me.  For one..why should it alter my Windows MBR if I want to boot from a floppy?  That isn't good and it isn't fun either.

> Since it appears that you are mixing SATA and IDE drives, that could be part of the problem. I think I've seen somewhere that when you have a IDE plugged in, it tries to take the top spot.

Yes, that would make sense, but the IDE drive IS in the top spot, it is the first drive.

> Other than that, once you have GRUB installed to the MBR of the correct drive, you need to make sure that your BIOS is set up to boot from that drive first. I know that it can get very confusing what drive is what if you start switching orders, but if you can get to the GRUB bootup menu, then you can edit the lines before you boot and that will definitely nail down whether it's looking at the wrong drive.

Ok, on the Dell machine I have, these are my booting options (meaning when you push the power button on you have your choices of these boot optons).

1) IDE Hard Drive C:
2) Floppy Diskette
3) IDE CD-Rom
4) USB

(You can change the boot priority though, so I can have BIOS boot from the USB first if I want and if there isn't anything there, it would move down the line until it hits a bootable operating system).

Upon boot up you also have the option to punch in F12 and from there I get these options:

1) Normal
2) SATA
3) Primary Master Drive
4) IDE Hard Drive C:
5) Floppy Diskette (I forgot to add this in past listings)
6) IDE CD-ROM
7) USB Bootable drive

So as you can see I have many more selections from punching in F12 and using the boot menu.  Notice that from the BIOS boot the ONLY hard drive selection I can make is IDE Hard Drive C:.

While this may seem stupid for a company to make a machine that has only this kind of boot option for a hard drive...keep in mind that it was only recently that Dell was supplying machines with Linux installed.  So for the longest time, Dell only had to make their machines boot into Windows.

Now with Windows on my machine, I can boot Normal, into the C: drive via the F12 menu.  Windows will also boot up upon power up.

However, with Grub installed, it seems to want to move the MBR to the Primary Master Drive designation.  Now I don't know what that is.  But the thing is that Normal boot and IDE Hard Drive Boot NO LONGER WORK, and produce the No operating system error.

However, going into F12 I can punch in the Primary Master Drive selection and Grub would come up and then I could boot into Windows or Linux.

So I guess the point I am trying to say is that I CAN'T boot from any other hard drive BUT the one that pointing to IDE Hard Drive C:

Now I don't know what would happen if I pull the IDE drive and just boot to the SATA drive.  This option COULD change.  In fact I did want to try a test by attempting to load 64Studio back on the SATA drive BUT WITH THE WINDOWS IDE DRIVE PULLED.  This way Grub would have no choice but to install elsewhere AND it shouldn't mess with the Windows MBR.


> Take a look at the links in my sig. This is how I am booting several distros at the same time by keeping GRUB in the MBR and GRUB's data in it's own partition. Once you understand what he has posted, you should never have to reinstall any bootloader ever again until your drive fails.

I will take a peek at it, but according to the way my system is set up, I have an odd-ball BIOS on my machine that wants to see something bootable on the IDE Hard Drive C:.  So if there isn't something there, then I can understand why I get the error message.

Overall, it seems to me that Grub is putting itself where it shouldn't be...in reference to my machine and it's BIOS.  Of course Grub doesn't care because the assumption is that I can change my Bios to a different bootable hard drive.  But the fact is I can't.

I really think that unless there is a sure fire way I can pull this off, I really don't want Grub (or any other bootloader for that matter) even touching the Windows boot MBR any more.  I would rather have a floppy boot up my Linux drive and keep away from the Windows MBR.

Can that be done?  Would the Super Grub floppy disk I made help?

The bottom line is that I would like to fix this situation so I can get back to making music and not fighting a bootloader program that keeps knocking out my Windows partition.

Thank You,

Geo

---

### Post by dstew on 2008-07-27
> Overall, it seems to me that Grub is putting itself where it shouldn't beMaybe the problem is not grub itself, but the 64Studio installer. Even with regular Ubuntu, grub does not install itself, but the installer's operating system (Linux) and installation program do it. Sometimes, it is that program making the mistake. Grub itself cannot alter the MBR of a disk unless you specifically direct it to do so with the setup command.

What I would do in your case is get away from having the installer install grub. Usually there is an option. At least in the regular Ubuntu installer, right before it installs grub, there is a sceen with an Advanced tab, and you can choose not to install the boot loader at all. That is the best way to go if the installer keeps making a mistake when installing grub. Then, boot a real plain grub floppy, and install grub from there exactly where you want it to go. Grub has an auto-complete feature that lets you get directory listings, and drive geometry, so you can figure out exactly which drive is which before you set it up.

I am not familiar with Ubuntu 64Studio. Maybe they have a forum that you can post on.

---

### Post by jukingeo on 2008-07-27
> **dstew said:**
> Maybe the problem is not grub itself, but the 64Studio installer. Even with regular Ubuntu, grub does not install itself, but the installer's operating system (Linux) and installation program do it. Sometimes, it is that program making the mistake. Grub itself cannot alter the MBR of a disk unless you specifically direct it to do so with the setup command.

What I would do in your case is get away from having the installer install grub. Usually there is an option. At least in the regular Ubuntu installer, right before it installs grub, there is a sceen with an Advanced tab, and you can choose not to install the boot loader at all. That is the best way to go if the installer keeps making a mistake when installing grub. Then, boot a real plain grub floppy, and install grub from there exactly where you want it to go. Grub has an auto-complete feature that lets you get directory listings, and drive geometry, so you can figure out exactly which drive is which before you set it up.


Hello dstew,

I will give you an update on what has been going on.  Yesterday (as you know) I did try to create a boot floppy and have grub install there, yet something disasterous happened again and once again I found myself reinstalling Windows.

So I got Windows going again last night and today I decided to try an experiment (as suggested by a fellow Ubuntuer).

I decided to physically disconnect the Windows drive completely and shut off the primary IDE connection in my Bios.

I then booted up the machine and loaded on 64Studio.

After the installation I DID look on the Grub bootloader menu and it only gives you four options.  I am pulling this from memory so it wasn't exactly written like this:

1) Install to the Primary Master MBR
2) Install to from another partition (I don't remember)
3) Install USB
4) Install to floppy

There wasn't an option to NOT install Grub.  So being that I did want to later on boot from a floppy, I selected that option.  Would you believe it wouldn't allow me to make a floppy boot???!!!  It bounced back with an error message saying that because I have one hard drive that it insisted that I set it up on the primary master MBR.  At first I thought the problem was due to the fact that I hadn't erased the floppy drive, BUT the thing is that when I selected the floppy drive, the Grub installer DIDN'T bother to even scan the floppy drive (evident by the floppy drive light not coming on).

Anyway, I proceeded with the only option I could and that was an MBR install of Grub.

When it was done, the machine rebooted and at first the Grub screen came up for a short time and then went straight into 64Studio.  I then went for a complete shutdown and then turned on the machine for a cold boot...FLAWLESS!

So now I am beginning to believe that the old version of Grub on 64Studio was more or less built for a single drive install.

So I did get to wondering if I should put both Windows & 64Studio on one hard drive.  But I am not sure.

At any rate I went into Bios to see what was happening now that I only had the Sata drive hooked up.  I expected the "IDE Hard Drive C:" designation would change.  Guess what? It didn't.  In fact my boot order list was identical as for the multi-drive setup:

1) IDE Hard Drive C:
2) IDE CD-Rom
3) Floppy Diskette
4) USB Bootable drive

However there was an entry missing from the F12 Menu:

1) Normal
2) SATA
3) IDE Hard Drive C:
4) Floppy Diskette
5) IDE CD-Rom
6) USB Bootable Drive.

Yeah, the Primary Master Drive listing was gone.

Now remember that with the dual drive setup THIS was the only hard drive selection that worked from the F12 menu.  Nothing else worked and yeilded the Cannot Find OS error.

Now with the single SATA drive, I am able to boot into all three of the first selections without a problem.

So something is really funky going on.

But as of now, I know that I would have to make some serious alterations to Grub because it is now seeing the SATA drive as the main drive (HD0,0).  So I KNOW I can't just simply hook up my Windows drive again and expect it to work.

Anyway, I do have also an outside fellow that is helping me and he is assisting me with updating Grub to the version Ubuntu uses and hopefully that can correct my problem.  He believes the fault is lying in the older version of Grub that 64Studio comes with.

> I am not familiar with Ubuntu 64Studio. Maybe they have a forum that you can post on.

Yeah, they do have a forum, but it is kind of poorly laid out and most of the guys there are pretty much on an exclusive 64Studio setup.  As I proved this morning, if that is the case then the installation works flawlessly.  But I have a dual boot with mixed drives and a BIOS that doesn't want to change a hard drive boot up from anything BUT IDE Hard Drive C:  So I am kind of a 'special case'.

I just figured that because this is mainly a Grub issue that my buddies here at Ubuntu could help me out.  This is just such a WIDE support base here and answers come fast.

But I know that if this last trick doesn't work out, I am probably going to put Ubuntu Studio back on.  I know Hardy has it's problems, but I do know that it is being worked on.

The guy's reasoning over at 64Studio as to why they are using an older version of Grub is because of stability.  But apparently they didn't take into account the many situations that happen when one wants to dual boot.  So that is where the help falls a bit short.

At any rate, I will report back if installing the new Grub is a success.

Geo

---

### Post by dstew on 2008-07-27
Thanks for the update. It is strange your BIOS seems to detect if you have the SATA drive in there, at least on the F12 menu, but then does not have the option in the regular BIOS setup. It could be a BIOS bug. You might look into updating your BIOS.

Best wishes, dstew.

---

### Post by jukingeo on 2008-07-27
> **dstew said:**
> Thanks for the update. It is strange your BIOS seems to detect if you have the SATA drive in there, at least on the F12 menu, but then does not have the option in the regular BIOS setup. It could be a BIOS bug. You might look into updating your BIOS.

Best wishes, dstew.

Yeah, I found that strange too, but yet it CAN boot properly from the SATA drive.  It has to be because that is all I have in my machine right now (I disconnected the IDE Windows Drive completely).

Why the Bios is still labeling the drive partion as IDE Hard Drive C: is beyond me.  It isn't an IDE drive and it doesn't have a C: designation.  Yet the drive is booting up properly on start up.

I figured something like this would throw Grub for a huge loop, but instead with the single hard drive (AND being a SATA drive too) the installation was flawless.

But I can't continue to run like this becase I need my Windows applications too.  So a dual boot is a necessity.

At any rate I did download the Super Grub iso file for diskette and put it on a Floppy.  So I could go that route in the event the current plan doesn't work.

I was talking of another bootloader but everyone is still saying that I should stick with Grub or Super Grub and that all my problems were mainly because how the installer of 64Studio interacted with THAT version of Grub.

Apparently it doesn't know how to handle the IDE/SATA configuration I have.  So it sets it up the way it knows how.  The trouble is that the actual partition where Grub is, my computer can't boot to.

So I guess right now I am kind of taking it one step at a time.  I am kind of stuck right now just trying to find a way to make this work.

As I said, I am just waiting for a response from a fellow that is helping me out with updating Grub.  Since the Ubuntu Grub worked on my system, updating to that and configuring my drives manually SHOULS solve the problem.

But while hanging out in 64Studio, I been noticing the distro does peculiar things too and there are problems I have to straighten out there as well.  Those questions of course are specific to that distribution and I have left questions there.  But if 64Studio gives me more problems, I am probably going to come back to Ubuntu Studio.

Once again...we will see.  I will keep everyone posted once a solution presents itself that has a positive outcome.

Geo

---

### Post by jukingeo on 2008-07-28
Hello Dstew and all,

I thought long and hard about what has been going on the past few days and I wasn't getting anywhere with 64Studio.  While it may be a good operating system, I know that I am not ready to deal with the advanced problems.  On top of that, 64Studio doesn't have the support base that Ubuntu has.  So this morning I decided to to wipe it and my troubles with it off of my hard drive.

I am still looking into other alternatives, including an audio/video editing system based on Puppy Linux. (which does have good support BTW).  However, still being a beginner/novice, I realized that my problems here (with Ubuntu) were no where near as large as my problems with 64Studio (and it is true that I didn't have a compatible sound device then as I do now).  Given the great support that Ubuntu has to offer, I am more then likely going to come back to give it another go with Ubuntu Studio.

But this time I am going to heed the advice of others and go with a full install via DVD instead of installing Ubuntu and then doing the U-S upgrade.   Supposedly the full DVD install yields better results.  Well, we will see.

I am just going over my boot options as we speak because I do want to try a triple boot with Windows XP, Puppy Linux, and Ubuntu Studio.

I figured I will be spending a lot of time in Puppy, but I know the problems I had with Ubuntu the first time around are being worked on and hopefully by the next Ubuntu (Studio) incarnation, that I will see many more improvements.

But thanx anyway for helping as I believe it was the older version of Grub on the 64Studio CD that was causing all my problems.

It is the great support here at Ubuntu that pulled me right back.

Geo

---

