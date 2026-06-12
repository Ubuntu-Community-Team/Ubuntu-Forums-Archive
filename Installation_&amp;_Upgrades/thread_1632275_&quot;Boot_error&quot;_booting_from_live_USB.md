---
title: "&quot;Boot error&quot; booting from live USB"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by iilkevych on 2010-11-27
Env
I have intel motherboard(d102ggc2) and 4Gb flash drive.
I've created live USB using usb-creator-gtk(ubuntu 10.04)
There is no option "all fixed disks" in BIOS settings
([http://ubuntuforums.org/showthread.php?t=1616610](http://ubuntuforums.org/showthread.php?t=1616610))
Drive is formatted into FAT32 using GParted
([http://ubuntuforums.org/showthread.php?t=1167803](http://ubuntuforums.org/showthread.php?t=1167803))

Target
I'm tying to install ubuntu 10.10 or 10.04

Problem
I get "Boot error" when booting using live USB.
There are only two words(please let me know if i can get any other logs).
Issue is not reproducible on other env(hp625 and other desktop).

---

### Post by Quackers on 2010-11-27
Welcome to UF :-)
I am a little unclear here. Is there an option in your bios to boot from a usb flash drive? If there is no such option you cannot boot from one on that machine.

---

### Post by oldfred on 2010-11-27
Do you have a boot flag on the USB partition?

Some intel boards/BIOS will not even let you start to boot unless you have a boot flag. Windows requires one on a primary partition. Grub does not use a boot flag.

---

### Post by iilkevych on 2010-11-29
Thanks for replies.

@Quackers
to select device to boot from i press F10 select my USB drive and booting starts and immediately fail with "Boot error"

@oldfred
I can see in GParted boot flag
I'm running ubuntu 10.04 on env where i want to boot from usb

---

### Post by oldfred on 2010-11-29
Seems more like a BIOS error as if USB does not have boot in MBR.

Do either of these apply:
syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

---

### Post by blacksunseven on 2011-01-03
I'm encountering the same trouble as the OP. I've tried creating a bootable USB flash drive containing Server 10.04LTS and have had no luck. I've confirmed that the drive does not boot by testing it on multiple machines that I know to be capable of USB booting (in fact, I've done this process before.. successfully). I've tried using unetbootin and usb-creator-gtk under Maverick 10.10 desktop as well as the universal usb creator binary in Windows 7. All complete successfully but do not function. I should mention, at this point, that I've both used the BIOS boot menu and have tried configuring the boot order in the BIOS (where I disabled all devices minus the USB flash drive) and continue to encounter the "insert proper boot disk" error. I then thought it might be something to do with the size of the flash drive (16GB, Mushkin Mulholland) and created a partition map of a bootable FAT32 partition using disk utility in Maverick, 2.5GB in size. I left the remainder of the disk unpartitioned. I'm quite puzzled as to what is going wrong here. I've done research on my flash drive and have seen people citing is as being bootable (even specifically with Ubuntu) without issue.

---

### Post by oldfred on 2011-01-04
If the syslinux bug solutions do not help, I cannot help either. 

I actually use grub2 to boot (loopmount) all my ISOs. I have  a 4GB Flash drive with several versions of Ubuntu and repair ISO and a full install of Ubuntu on my 16GB Flash with one or two extra grub2 entires for booting ISOs. I find it quicker & easier just to edit a grub entry and just copy ISO to Flash drive.


 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
With grub2 persistant C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
multicd.sh - combine Linux ISOS into one
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

### Post by blacksunseven on 2011-01-05
> **oldfred said:**
> If the syslinux bug solutions do not help, I cannot help either. 

I actually use grub2 to boot (loopmount) all my ISOs. I have  a 4GB Flash drive with several versions of Ubuntu and repair ISO and a full install of Ubuntu on my 16GB Flash with one or two extra grub2 entires for booting ISOs. I find it quicker & easier just to edit a grub entry and just copy ISO to Flash drive.


 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.


Whoa, lots of information. I've just finished attempting the information in the above quoted link without any success. If grub2 won't load this .iso for Ubuntu Server, I'm starting to think it's just plain not bootable.

Edit: I forgot to mention that I also burned the damn thing to a CD and connected it via USB and tried booting it that way (a complete waste of time and a total PITA) and that wouldn't boot either.

Edit 2: Just checked the md5 sums to make sure they match and this wasn't a really simple error - they match.

Edit 3: Just wasted an inordinate amount of time trying to use this method:
> **oldfred said:**
> [http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 


That script doesn't work, despite it looking very pretty. Think I've had enough for tonight..

Edit 4: Okay, so maybe I tried one more thing. I tried using the 10.10 Desktop AMD64 ISO and had zero luck with that either. Is it possible something is wrong with my flash drive? I did fail consistency checks when using usb-creator-gtk on more than one occasion (though recovered).

Edit 5: Finally got it bootable using this method here [http://www.mushkingames.com/phpbb2/viewtopic.php?f=27&t=14880&sid=104a446aab22ea8e50f2e6c73d1d0b74](http://www.mushkingames.com/phpbb2/viewtopic.php?f=27&t=14880&sid=104a446aab22ea8e50f2e6c73d1d0b74). Hasn't helped in getting Ubuntu to boot from it though. I'm curious why usb-creator-gtk and unetbootin did not work...

---

