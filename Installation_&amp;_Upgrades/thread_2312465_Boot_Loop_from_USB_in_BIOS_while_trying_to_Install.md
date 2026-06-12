---
title: "Boot Loop from USB in BIOS while trying to Install ubuntu"
date: 2016-02-04
forum: Installation &amp; Upgrades
---

### Post by Raymond_Carl on 2016-02-04
Hi,

Trying to install Ubuntu 64 on a ASUS EeeBook X205TA that is currently running Windows 10.

I have followed the instructions to create a bootable USB, which seems to be ok (see screenshot).  When I go into the bios and select the option to boot from the USB, it looks like it tries to boot from the USB and then goes right back to the BIOS no matter how many I try it.  I cannot tell if it's an issue with the boot image or if it is some control placed on the bios preventing people from installing a new OS, or some completely different issue.

I saw a previous thread where someone gave a solution that worked related to deselecting the USB as a harddrive in the BIOS menu, but I don't have any harddrive options in bios menu (posted a screen shot too).

Instructions I followed to create a USB:
[SIZE=2]http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/
[/SIZE][SIZE=2]

[/SIZE]&#8203;

---

### Post by oldfred on 2016-02-04
I think this is a 32bit UEFI on a 64bit system, to prevent other installs. But then soon after Linux developed a 32bit UEFI boot, but that is not standard.

 Asus X205TA hardware support in Ubuntu 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2254322](http://ubuntuforums.org/showthread.php?t=2254322)
      
 New Intel Atom - Nov 2013 x86 secure boot can be turned off, but only 32 bit UEFI which no one else has.
 Intel Atom SoC systems that ship with Windows 8/8.1 32-bit provide 32-bit UEFI-only firmware with no BIOS compatibility option (no CSM). In UEFI terms these systems are called Class 3 systems (this term is not specific to 32-bit), ie. UEFI-only with no BIOS CSM.
Windows with Atom 
[http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux](http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux)

---

### Post by Raymond_Carl on 2016-02-04
Thanks Oldfred.  I'm not that advanced of a user, but that means that installing a 32 bit version of Ubuntu might work?  It is definitely a 64 bit machine, but I think they install a 32bit OS because of the low RAM.  Maybe the UEFI is 32bit to prevent OS changes?

I checked out the first link you sent, and it seems like it could be quite complicated on this machine?  The second link suggests it might not be possible though?

---

### Post by Raymond_Carl on 2016-02-04
Oh, I checked out the 3rd link you sent.  Seems like it could be quite complicated for a novice to pull off?

---

### Post by oldfred on 2016-02-04
It is not quite as complicated as it was, but still not easy.
The 32bit version of Ubuntu does not include UEFI boot.
So you have to get the 64 bit version and convert from 64 bit UEFI to 32 bit UEFI.
It used to be that you had to compile your own, but now it exists as a complied version.
But still not totally straight forward.

This one has a link to the 32bit UEFI file.
UEFI flash drives boot from /EFi/Boot/bootx64.efi, so you have to copy it into /EFI/Boot and rename it. Not sure about other details.
[https://sturmflut.github.io/linux/ubuntu/2015/01/21/installing-ubuntu-15.04-on-baytrail-tablets/](https://sturmflut.github.io/linux/ubuntu/2015/01/21/installing-ubuntu-15.04-on-baytrail-tablets/)

---

### Post by vladan_81 on 2016-04-14
I posted complete set of instructions on how to install Lubuntu 15.10 on X205TA. To fix your problem, see step 5 in the following link:
[http://ubuntuforums.org/showthread.php?t=2254322&page=91&highlight=X205TA](http://ubuntuforums.org/showthread.php?t=2254322&page=91&highlight=X205TA)

---

