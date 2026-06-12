---
title: "XP/Ubuntu, adding Vista to the mix"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by Dillius on 2007-06-18
I've been running Ubuntu with Windows XP now for a few years, and have never really had issues with dual booting due to the fact that I install them on separate hard drives.

Now I find myself needing to triple boot with vista, and would like to be able to do such without having to reinstall all 3 operating systems. Most of my time spent googling has led to no explanations of a situation like this without reinstalling all in a certain order, and typically on one hard drive. So I have a few questions and would be very grateful for any advice/answers.

Firstly, with Windows XP and Ubuntu on separate hard drives, and the partition I plan to install Vista onto on the drive with XP, will I have any hard drive issues?

Will my boot loader be changed over to Vista's boot loader when installed? If so, will Ubuntu be added as an option automatically? Is there a way I can prepare to add it when installation is complete manually? Can I switch back to GRUB as my bootloader(preferred course of action)? If so, is there a guide somewhere to show me how to add Vista to GRUB? Or perhaps an automated tool?

Any help is greatly appreciated.

---

### Post by joe.turion64x2 on 2007-06-18
Perhaps you can get a third hard drive and plug it in only when you want to use Vista, that way Vista will 'think' it is alone, and you would not mess up your existing installation. Perhaps a USB external drive might work for you.

Joe.

---

### Post by zackf on 2007-06-18
If Vista is on a third hard drive, I have seen posts on adding (or re-adding) Grub the MBR of the master drive, that shouldn't mess any of the data up. You probably want to verify that from someone smarter than linux than me though :-)

---

### Post by joe.turion64x2 on 2007-06-18
My suggestion of Vista in a third drive was to 'isolate' it and make him think he was the only OS there (no GRUB whatsoever). Assuming he wouldn't use Vista extensively it shouldn't be a problem to connect the Vista hard drive (and unplug the others) only when Vista was to be used.

Joe.

---

### Post by Dillius on 2007-06-19
My thoughts are that eventually Vista will be primary, and I'll remove XP. I'm sure that between now and then I'd do a full clean format, but I'd like to use the partition structure I already have available (I have a partition already on the drive with the XP installation for Vista). With ubuntu on the other hard drive, and no non NTFS partitions on the drive, would Vista have any problems with XP there? I could always unplug the Ubuntu drive when i install vista, then plug it back up after Vista is installed. Then I would just need a way to add vista to GRUB(unless grub directed to the vista bootloader in place of XP)

---

### Post by Dillius on 2007-06-19
Bump, still looking for anyone who has experience with this situation.

---

### Post by chadlewis on 2007-06-19
I've done this several times on two different machines now.

> Firstly, with Windows XP and Ubuntu on separate hard drives, and the partition I plan to install Vista onto on the drive with XP, will I have any hard drive issues? 

This is nearly identical to my setup, and I didn't have any problems. 

> Will my boot loader be changed over to Vista's boot loader when installed? 

Yes.

> If so, will Ubuntu be added as an option automatically? 

No.

> Is there a way I can prepare to add it when installation is complete manually? 

Use Super GRUB Disc to restore your GRUB.

> Can I switch back to GRUB as my bootloader(preferred course of action)? 

Yes. See above.

> If so, is there a guide somewhere to show me how to add Vista to GRUB? Or perhaps an automated tool?

[Super GRUB Disc]("http://supergrub.forjamari.linex.org/").

Basically what's going to happen is your GRUB boot loader will be restored, but only show one option for Windows, probably named for your Windows XP option. Select that option and you'll be taken to the Vista boot loader, which will allow you to select one of your two Windows installations.

Kinda sucks having to deal with two boot loaders, I know, but I haven't found an easier way, unless you want to go the virtualization route. I recommend [VirtualBox]("http://www.virtualbox.org/"). I had one minor hangup with the network driver, but other than that my vbox Vista has been running perfectly within Feisty.

---

### Post by Dillius on 2007-06-19
I have no problem using two boot loaders, I don't reboot very often anyways. Thank you all for your help.

---

### Post by Dillius on 2007-06-19
Actually running into more problems than I anticipated. 

Vista and XP are working fine, but I can not get GRUB restored correctly. I have it coming up, but it will not go to anything when i select my old Windows XP installation. It says something about having selected an invalid executable or something.

Thankfully, my BIOS allows me to choose boot order of hard drives, so I was able to switch through the bios, but I'm not sure what to do now that super grub disk didn't work.

Any advice on this matter would be appreciated, or I can just reinstall Ubuntu and it should detect them properly shouldn't it?

---

### Post by confused57 on 2007-06-19
> **Dillius said:**
> Actually running into more problems than I anticipated. 

Vista and XP are working fine, but I can not get GRUB restored correctly. I have it coming up, but it will not go to anything when i select my old Windows XP installation. It says something about having selected an invalid executable or something.

Thankfully, my BIOS allows me to choose boot order of hard drives, so I was able to switch through the bios, but I'm not sure what to do now that super grub disk didn't work.

Any advice on this matter would be appreciated, or I can just reinstall Ubuntu and it should detect them properly shouldn't it?
If you decide to reinstall Ubuntu, go into bios setup before installing and select your Ubuntu drive to boot before  your Windows' drive...grub should then be installed to the Ubuntu drive's mbr and entries should be added to boot XP and Vista on your other drive.

If you want to try to boot XP & Vista with your current Ubuntu install, post your menu.lst:
```
gedit /boot/grub/menu.lst
```
and
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by Dillius on 2007-06-19
gedit /boot/grub/menu.lst

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
timeout		10

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
# kopt=root=UUID=f6d1a149-8ba5-499b-9821-489d78554db1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f6d1a149-8ba5-499b-9821-489d78554db1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f6d1a149-8ba5-499b-9821-489d78554db1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f6d1a149-8ba5-499b-9821-489d78554db1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f6d1a149-8ba5-499b-9821-489d78554db1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```



sudo fdisk -l
(/dev/sdb1 is where Ubuntu resides)

```
Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        3264    26210047+   f  W95 Ext'd (LBA)
/dev/hdb2   *        3265       16318   104856255    7  HPFS/NTFS
/dev/hdb3           16319       24792    68067405    7  HPFS/NTFS
/dev/hdb5               2        3264    26210016    7  HPFS/NTFS

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2490    20000893+  83  Linux
/dev/sdb2   *        2491        2988     4000185   82  Linux swap / Solaris
/dev/sdb3            2989       60801   464382922+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   83  Linux

```

---

### Post by confused57 on 2007-06-19
I should have asked for your device.map in my other reply:
```
gedit /boot/grub/device.map
```

You said you were able to boot XP/Vista with no problems, is this with the Vista bootloader?  Are you able to boot into Ubuntu OK?

---

### Post by Dillius on 2007-06-19
(hd0)   /dev/hdb
(hd1)   /dev/sda
(hd2)   /dev/sdb
(hd3)   /dev/sdc

Yea Vista's bootloader i can default to with my BIOS, and it loads Vista and XP both fine. Also no, Ubuntu no longer loads from GRUB, though Super Grub Disc can load it.

I've wondered for a WHILE where these references were, now GRUB makes a bit more sense. Still welcome your advice however.

---

### Post by confused57 on 2007-06-19
> **Dillius said:**
> (hd0)   /dev/hdb
(hd1)   /dev/sda
(hd2)   /dev/sdb
(hd3)   /dev/sdc

Yea Vista's bootloader i can default to with my BIOS, and it loads Vista and XP both fine. Also no, Ubuntu no longer loads from GRUB, though Super Grub Disc can load it.

I've wondered for a WHILE where these references were, now GRUB makes a bit more sense. Still welcome your advice however.
I hope your bios is able to boot first to your sdb drive...if it is, you can use the live cd to install grub to it's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
This would involve booting the live cd(or you could use Super Grub Disk, by pressing "c" to get to a grub prompt), open a terminal:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd2,0)", you would then need to enter:
```
root (hd2,0)
setup (hd2)
quit
```

then boot first to your sdb drive, if you get a grub menu, highlight your Ubuntu entry, press "e", change root from (hd2,0) to (hd0,0), then press "b" to boot...this change is temporary, but you can make it permanent if it works.  (Note:  You need to press "e" again to change your root entry after it's highlighted).

If you're not able to boot first to your sdb drive or you just prefer having grub on your hdb mbr,  you could install grub to your IDE drive's mbr or "setup (hd0)"...your Window's entry in grub "should" work, I'm not sure.

---

### Post by Dillius on 2007-06-20
I actually just played around with it for a bit and fixed GRUB by changing all the (hd2, 0)'s over to (hd0, 0)'s for the ubuntu kernels and changing the windows entry over to (hd1, 1).

It successfully goes from Grub to Ubuntu or the windows bootloader now, but I can not continue out of the windows bootloader onto either version of windows, which makes me think i now need to figure out how to edit it properly.

---

### Post by confused57 on 2007-06-20
> **Dillius said:**
> I actually just played around with it for a bit and fixed GRUB by changing all the (hd2, 0)'s over to (hd0, 0)'s for the ubuntu kernels and changing the windows entry over to (hd1, 1).

It successfully goes from Grub to Ubuntu or the windows bootloader now, but I can not continue out of the windows bootloader onto either version of windows, which makes me think i now need to figure out how to edit it properly.

Your Window's entry would need mapping commands:
```
title  Windows XP
root  (hd1,1)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

You might also need to change your device.map:
```
(hd0) /dev/sdb
(hd1) /dev/hdb
```
to get it to work, or possibly not?

If you decide to leave your system set up this way, be sure to change the line with groot to (hd0,0)...

---

### Post by Dillius on 2007-06-20
I'm going to try adding the mapping commands now. I don't need to change the device.map i'm quite sure now, as they are pointing at the right places, the only thing wrong now is that once i get to the Windows Bootloader it restarts the computer whenever I pick either XP or Vista. If i change over to that hard drive as my first load, the bootloader works. The mapping should do the trick I hope.

What do you mean by changing the groot to (hd0, 0)? Don't know what that is.
EDIT: Correction. Just found groot in my menu.lst. It's commented out?

---

### Post by confused57 on 2007-06-20
> **Dillius said:**
> I'm going to try adding the mapping commands now. I don't need to change the device.map i'm quite sure now, as they are pointing at the right places, the only thing wrong now is that once i get to the Windows Bootloader it restarts the computer whenever I pick either XP or Vista. If i change over to that hard drive as my first load, the bootloader works. The mapping should do the trick I hope.

What do you mean by changing the groot to (hd0, 0)? Don't know what that is.
EDIT: Correction. Just found groot in my menu.lst. It's commented out?

This explains how groot is utilized in menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

This is one instance where the # doesn't actually comment out the entry, leave the # in front of groot.

---

### Post by Dillius on 2007-06-20
Alright, I'll get that changed around next chance I get.

Aside from that everything is working perfectly now, thanks again for your help.

---

### Post by confused57 on 2007-06-20
> **Dillius said:**
> Alright, I'll get that changed around next chance I get.

Aside from that everything is working perfectly now, thanks again for your help.

Glad to help & that it worked...

---

