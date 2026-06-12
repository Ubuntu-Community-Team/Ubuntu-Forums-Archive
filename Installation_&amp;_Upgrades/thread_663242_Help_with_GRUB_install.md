---
title: "Help with GRUB install"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by djpandemonium on 2008-01-09
I've done a bit of googling and searching, and found a ton of material on the topic, but nothing yet that solves my problem.

First off my setup:
P4 2.4 w/2gigs of RAM.
Two hard drives:
IDE 250gig Data drive
SATA 80gig OS drive.

The IDE drive has one NTFS partition (for now).  
The SATA drive has three partitions:
40gig NTFS with Windows XP
36gig ext3 with Ubuntu mounted as /
4gig swap

Ubuntu sees it as the following:
250gig drive: sda1
40gig WinXP partition: sdb0
36gig Ubuntu partition: sdb1

When installing Ubuntu 7.10 from the live CD, if I just choose the default config (GRUB installed on hd0), then it's successful, however upon reboot it doesn't start GRUB, it just starts straight into WinXP.  I'm guessing that is because hd0 might refer to the IDE drive instead of the SATA drive where it needs to install it...?

Not knowing much about GRUB, I reinstalled but told it to install grub at hd1 this time.  When I reboot it comes up with a GRUB menu with all the Ubuntu options listed, as well as WinXP.  When I choose any of the Ubuntu options, it gives me an error about the partition not existing.  If I choose WinXP, then it says ntldr is missing.

I repaired the Windows boot loader which let me back into Windows, but still no GRUBby goodness to get my Ubuntu on.  Any help would be much appreciated!

---

### Post by Shazaam on 2008-01-09
Try this page....
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by djpandemonium on 2008-01-09
Thank you.

I get this far:
grub> find /boot/grub/stage1

And it says it that it's not found.

---

### Post by confused57 on 2008-01-09
Have you tried setting your bios to boot your IDE drive before your SATA?

---

### Post by djpandemonium on 2008-01-10
True story:  I was about to type a reply stating as politely as I could that doing so would be ludicrous, seeing as how my OSes aren't installed on that drive.

I got halfway through the sentence, and realized that you're actually quite clever instead of mildly clueless yet helpful.  ;-)

So, I did as you said, and it works.  The MBR is installed on the IDE drive, and it works just fine there booting to the OSes on the other drive.

So, thank you.

Now, how can I get GRUB installed on the correct drive?  That way if the IDE drive dies, or I need to otherwise change it, I'm not back where I started?

---

### Post by confused57 on 2008-01-10
> **djpandemonium said:**
> True story:  I was about to type a reply stating as politely as I could that doing so would be ludicrous, seeing as how my OSes aren't installed on that drive.

I got halfway through the sentence, and realized that you're actually quite clever instead of mildly clueless yet helpful.  ;-)

So, I did as you said, and it works.  The MBR is installed on the IDE drive, and it works just fine there booting to the OSes on the other drive.

So, thank you.

Now, how can I get GRUB installed on the correct drive?  That way if the IDE drive dies, or I need to otherwise change it, I'm not back where I started?

Usually when there is a combination of IDE and SATA drives, grub is installed to the IDE mbr, regardless if the SATA drive is first in boot order.  I would recommend that you continue to boot to your IDE drive...if Ubuntu fails, you can always change your boot order to SATA first, in order to boot into Windows.

You can install grub to the SATA drive's mbr, using the live cd(rather than reinstalling):
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
you would need to "setup (hd1)"

Change your bios to boot first to the SATA drive, make sure your Ubuntu entry is highlighted in the grub boot menu, press "e", select the line with root, change root from (hd1,1) to (hd0,1), press "enter", then "b" to boot...this is temporary, but if it works you can make it permanent in your menu.lst...your Windows entry should be root (hd0,0).

---

### Post by djpandemonium on 2008-01-10
The problem is that this silly Dell BIOS doesn't seem to give me the option in the the actual BIOS page to choose WHICH drive it boots first.  Just that I want it to boot up a hard drive first.

The only way to choose whether I want that drive to be SATA or IDE is to hit F12 during post to get the boot menu and select it there.  But, I don't want to have to do that each and every time I boot/reboot the machine, so I think it best that I put GRUB on the OS drive.

I've got a bunch of homework to finish up tonight, so I'll tackle that one tomorrow.  Thank you very much for your help thus far.  :-)

---

### Post by confused57 on 2008-01-10
> **djpandemonium said:**
> The problem is that this silly Dell BIOS doesn't seem to give me the option in the the actual BIOS page to choose WHICH drive it boots first.  Just that I want it to boot up a hard drive first.

The only way to choose whether I want that drive to be SATA or IDE is to hit F12 during post to get the boot menu and select it there.  But, I don't want to have to do that each and every time I boot/reboot the machine, so I think it best that I put GRUB on the OS drive.

I've got a bunch of homework to finish up tonight, so I'll tackle that one tomorrow.  Thank you very much for your help thus far.  :-)

One of my pc's is a Dell Dimension 4550, which can only boot to the primary master drive, so I can understand where you're coming from.  See my last reply to install grub to the SATA drive's mbr, using the Ubuntu live cd...reboot your Dell, try using the "e" method I described, replacing (hd1,y) to (hd0,y), y meaning leave this value as it is.

If your computer boots OK, then you can make it permanent:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
change your Ubuntu entrys' root from (hd1,y) to (hd0,y) and also change the line with #groot to (hd0,y):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
change your Windows entry to root (hd0,0)
quit & save

You might also need to change your device.map:
```
gksudo gedit /boot/grub/device.map
```
change:
```
(hd0) /dev/sda
(hd1) /dev/sdb
```
to show:
```
(hd0) /dev/sdb
(hd1) /dev/sda
```
again, quit & save

Good luck with it.

---

### Post by djpandemonium on 2008-01-10
Thank you very much for your help again.

I just finished going through your directions, and we're almost there.  GRUB is booting Ubuntu fine when I set it to (hd0,1), however with it set to boot WinXP from (hd0,0) I get the dreaded:
```
NTLDR is missing
```

---

### Post by djpandemonium on 2008-01-10
I just took a peek at the fully-working GRUB install on the IDE drive, and it is set to boot WinXP as (hd0,0), so I have no idea why the SATA GRUB install won't boot it correctly when it's set the same...

---

### Post by confused57 on 2008-01-10
> **djpandemonium said:**
> I just took a peek at the fully-working GRUB install on the IDE drive, and it is set to boot WinXP as (hd0,0), so I have no idea why the SATA GRUB install won't boot it correctly when it's set the same...

I found this on Herman's site about editing the device.map, which may be needed to boot  Windows:
[http://users.bigpond.net.au/hermanzone/p15.htm#device.map](http://users.bigpond.net.au/hermanzone/p15.htm#device.map)

You might want to post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

This will show if the bootflag is on(*) for your Windows partition.

---

### Post by djpandemonium on 2008-01-10
Here is the fdisk output whilst I do the stuff on that link:
```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13fc13fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd032d032

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4862    39053983+   7  HPFS/NTFS
/dev/sdb2            4863        8997    33214387+  83  Linux
/dev/sdb3            8998        9726     5855692+  82  Linux swap / Solaris

```

---

### Post by djpandemonium on 2008-01-10
So, I'm assuming I don't need to make further changes to the device.map, because we already did that.

So, I try to follow the rest of his directions, but to me they don't make much sense.  His first step after changing device.map is to do this:

```
herman@amdxz:~$ grub --device-map=/boot/grub/device.map
```

But, then in the next step he seems to have forgotten that he told you to do the first one, and thinks you are still at a shell prompt rather than the grub prompt:

```
herman@amdxz:~$ sudo grub
```

If I skip the first step, then I go through the whole process, and end up no different than I was before.  If I skip the second step, then it fails when I do this:
```
grub> root (hd1,1)
```
telling me that it doesn't exist.

And, if I try to do it exactly as he put it, then it errors at the second command telling me "Unrecognized command" because sudo obviously doesn't mean anything to GRUB.

---

### Post by confused57 on 2008-01-10
After you have run:
```
grub --device-map=/boot/grub/device.map
```

Does "sudo grub" give you a grub prompt(grub>)?

If it does, then what does this command show?:
```
find /boot/grub/stage1
```

If it shows "root (hd0,1)", you could try:
```
root (hd0,1)
setup (hd0)
quit
```

---

### Post by djpandemonium on 2008-01-10
Running
```
grub --device-map=/boot/grub/device.map
```
gives me a grub> prompt.  So, I'm already at a grub> prompt, and I would have to quit back out to run sudo grub.

Is that what I'm supposed to do?  Run with the device-map option, do nothing other than quit, and then run sudo grub?  That doesn't seem like it would accomplish anything...

---

### Post by confused57 on 2008-01-10
> **djpandemonium said:**
> Running
```
grub --device-map=/boot/grub/device.map
```
gives me a grub> prompt.  So, I'm already at a grub> prompt, and I would have to quit back out to run sudo grub.

Is that what I'm supposed to do?  Run with the device-map option, do nothing other than quit, and then run sudo grub?  That doesn't seem like it would accomplish anything...
After you run the first command, then "quit" to exit the grub shell, then run:
```
sudo grub
find /boot/grub/stage1
```
post back what this shows

---

### Post by djpandemonium on 2008-01-11
It shows: 
```
(hd1,1)
```

---

### Post by confused57 on 2008-01-11
Seems you're not the first to get "ntldr missing" with IDE + SATA drives:
[http://ubuntuforums.org/showthread.php?t=508135&highlight=ntldr](http://ubuntuforums.org/showthread.php?t=508135&highlight=ntldr)

Your best bet might be to use the XP cd, run FIXMBR to restore Windows IPL to the SATA drive's mbr...make sure Windows boots OK.  Then disconnect your IDE drive & reinstall Ubuntu.

I wish I could help you with a better solution...reading through  threads with "ntldr missing", I haven't really found a definitive answer.

It's obvious your ntldr isn't missing, since you were previously able to boot Windows from grub on your IDE mbr and FIXMBR worked.

[http://users.bigpond.net.au/hermanzone/p15.htm#NTLDR_is_missing_press_any_key_to](http://users.bigpond.net.au/hermanzone/p15.htm#NTLDR_is_missing_press_any_key_to)
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

Added:  Please post your current menu.lst:
```
gedit /boot/grub/menu.lst
```
you just need to post your entries to boot Ubuntu & Windows

---

### Post by djpandemonium on 2008-01-11
Woops!
I was so anxious to get the thing working, that as soon as I saw you say I should reinstall, I started the process.  I just got back from it.  I don't know if you still want my menu.lst...?

I actually didn't bother to restore the Windows MBR.  I just flipped off the machine, unplugged the IDE drive, booted up to the live CD and reinstalled, turned off the machine, and reconnected the IDE drive.  Now everything works exactly as it should: it is booting from the SATA MBR and I can boot into WinXP or Ubuntu, as well as see all drives and partitions from within the OSes.

Is there anything I should post here now that it's working that would tell us what we should have done?  Maybe we could at least make this useful for the next guy with the same problem....

---

### Post by confused57 on 2008-01-11
> **djpandemonium said:**
> Woops!
I was so anxious to get the thing working, that as soon as I saw you say I should reinstall, I started the process.  I just got back from it.  I don't know if you still want my menu.lst...?

I actually didn't bother to restore the Windows MBR.  I just flipped off the machine, unplugged the IDE drive, booted up to the live CD and reinstalled, turned off the machine, and reconnected the IDE drive.  Now everything works exactly as it should: it is booting from the SATA MBR and I can boot into WinXP or Ubuntu, as well as see all drives and partitions from within the OSes.

Is there anything I should post here now that it's working that would tell us what we should have done?  Maybe we could at least make this useful for the next guy with the same problem....

Great, glad you got it working...you were a couple of steps ahead of me.

I'm not sure if it would help or not, but you might want to post your menu.lst & device.map:
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```

I just think originally grub was trying to boot your storage partiton on sda1, giving you the "ntldr missing" error...it should have been reparable with modifications in grub, but I wasn't sure what you needed to do.

---

### Post by djpandemonium on 2008-01-11
Yeah, it definitely seems like it was trying to boot from the wrong place, doesn't it.

Here is the menu.lst from the working install:
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
# kopt=root=UUID=f9716c84-ef08-4c4b-bd8d-029509da1ac4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f9716c84-ef08-4c4b-bd8d-029509da1ac4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f9716c84-ef08-4c4b-bd8d-029509da1ac4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

And, here is the device.map:

```
(hd0)	/dev/sda
```

It's interesting that the device.map doesn't even mention the other drive.  I wonder if that was (at least part of) our problem.

At any rate, thank you VERY VERY much for working through this with me!  You obviously put in some time researching to help me find the answers.  Thank you!

I'm new around here, is there any sort of rep points or anything I should be doing, or other official thanks?  They do that on some boards....

---

### Post by confused57 on 2008-01-11
It's really unclear to me how device.map is utilized for grub to boot various OSes, especially on different drives...thought it may help and was worth trying.  This is how I've set up a couple of my pc's:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
I've never had to add the 2nd hard drive with Windows to my device.map, the only thing listed in device.map is "(hd0) /dev/hda".

I'm just glad you were able to get your system set up...thanks isn't necessary, but it's nice to get positive feedback.  Here's a thread about a "thanks" button, that has recently been added to the forum:
[http://ubuntuforums.org/showthread.php?t=654837&highlight=thanks](http://ubuntuforums.org/showthread.php?t=654837&highlight=thanks)

I know you'll enjoy using Ubuntu as much as I, I've learned much more than I thought possible about Linux & computers.  You'll be helping others before you know it.

---

