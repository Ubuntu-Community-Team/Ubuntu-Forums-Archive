---
title: "Can't boot into Ubuntu after Feisty upgrade"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Miaowara on 2007-05-16
Hello.

I just upgrade to Feisty and am now unable to boot into Ubuntu. When I use the regular splash-screen enabled boot entry, the boot process seems to stop at the "root file system" item (mounting or something like that). When I use the recovery mode, I can get as far as the usb detection step at which point my usb keyboard and mouse are recognized and then the process stops. I noticed Ubuntu is now recognizing my hard drive as SCSI which I wasn't doing before (I was getting hda stuff rather than sda). Could this possibly be the problem? Is there any other way I can tell where the problem may lie?

thanks

---

### Post by SubGothius on 2007-05-16
I have found much, myself and mentioned elsewhere, in the way of sundry drive-detection weirdness going on with Ubuntu 7.04 "Feisty", possibly related to the adoption of SCSI drivers for all drives (including IDE), yet I haven't found any hint of a general-purpose workaround.

In my own case, [the Feisty installer failed to detect all but one of my drives, likewise for my complete Feisty system post-install](http://ubuntuforums.org/showthread.php?t=440592).  My system is entirely SCSI-2 (aka "Fast SCSI") built into the mobo, and out of 3 hard drives, a CD-ROM and a CD-R, Feisty could only find one hard disk to use (which all worked fine in Edgy, and still do work fine in my other OS).  The fact that lone accessible disk showed as /dev/sdc (instead of /dev/sda) shows that Feisty can at least tell there are other devices on the bus, even tho' it can't manage to use them (see thread linked above for boot-time kernel log messages showing how the other devices are detected and then promptly offlined).

Strangely, the one usable HDD showed up as /dev/sdc during install, but that same device became /dev/sdb post-install in the full system.  That unexpected change caused me the same sort of "could not find root filesystem" type of error that you got, until I noticed the device ID change within my boot-time kernel messages and changed my original kernel argument "root=/dev/sdc5" over to "root=/dev/sdb5" in my bootloader.  So I have a bootable system for now, but I'm still limited to using just this one drive.
](*,)

---

### Post by Miaowara on 2007-05-17
Hey SubGothius!

Thanks a lot for your suggestion. Modifying the grub kernel line from "hda" to "sda" worked perfectly (it didn't occur to me that I coudl do that). I'm not back in my [mostly working] Ubuntu installation! Now I just got to get the Nvidia drivers working again!

Unfortuneately I can't help you on your problem. I've only got one drive to worry about (though it does have many partitions!). Good luck and thanks again!

---

### Post by sinaen on 2007-06-25
hey i also have problems that the computer mounts the wrong disks in the wrong places.. or vice verca..

[http://ubuntuforums.org/showthread.php?t=483083](http://ubuntuforums.org/showthread.php?t=483083) look at my post and youll maybe recognize your problem?

---

