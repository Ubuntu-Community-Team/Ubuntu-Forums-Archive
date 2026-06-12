---
title: "unable to boot computer"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by nals on 2014-10-20
i have a amd fusion computer with phoenix tiano bios

i have tried to install various distros, but never managed to boot up, other than with debian stable (wheezy).

everything else either does not boot up, or fails after the first boot (with a grub prompt at best)

i recently installed xunbuntu and the same issue continues

however, i installed xubuntu on a external hdd via a different computer, and this external hard drive does boot up without problems

on the amd computer, i also tried running boot repair , which gives a message saying creating an EFI partition, but despite that , still does not boot up

i am not running any other OS on the computer, and chose "use entire disk" on istallation

appreciate any help to solve this long outstanding issue 

nals

---

### Post by Bucky Ball on 2014-10-20
So it gets all the way through the installation, you boot the machine and ... do you get to a menu with a selection of kernels, choose the top one then it dies? Black screen or the grub prompt or it varies?

---

### Post by nals on 2014-10-21
it varies, the current one with xubuntu 14-10 beta 2, i get a blank screen

nals

---

### Post by Bucky Ball on 2014-10-21
Why are you using 14.10??? Not released with and not a good place to start. Try 14.04 LTS or 12.04 LTS. They are the only supported releases currently.

---

### Post by nals on 2014-10-21
only reason being 14:04 did not work, and i thought perhaps the newest version mite have sorted out some things. if you think 14:04 will be easier to get working , happy to reinstall and take it from there. i have tried it and had the same problem

imo, is not a distro/version thing, as i have tried numerous versions/distros over the last two years , is something to do with the bios, EFI and grub
 
i do realise you want to clear the basics first, if you want me to install 14:04 and post what happens , happy to do it

nals

---

### Post by Bucky Ball on 2014-10-21
14.04 or 12.04 we know are stable. 14.10 could be unpredictable at the moment so yes, let's go with a known quantity. ;)

Have you tried going to the BIOS and switching EFI off and installing in BIOS mode? EFI is a Win thing anyhow and arrived with Win 7 and 8 primarily (and probably now Win 10 also). An innovation ... :-k

If you want to use EFI for some reason, then get into the BIOS and switch off faststart and secureboot and try reinstalling again.

---

### Post by nals on 2014-10-21
tks, wil reinstall 14:04 and revert

i do not want efi or anything else, i only want a pure linux system that works

problem with phoenix tiano bios on this computer is that most options seem to be locked 

secure boot is off

revert and let you know what happens after installation of 14.04, as i said earlier off a external hdd installed on another computer is working well. problem is when i install this or any distro on this computer

nals

---

### Post by nals on 2014-10-21
installed 14:04

with installer usb plugged in, only gives me option to boot to the usb

with usb removed, goes to the "f12" screen, where the only option is the hhd but is unable to boot up, and comes back to the same screen

what shld i do ?

tks

nals

---

### Post by Bucky Ball on 2014-10-21
Are you running in BIOS or UEFI mode?

---

### Post by nals on 2014-10-21
how do i check that ?

did look through bios setup but could not find anything. boot priority order just shows
floppy drive
drive0 hdd
usb cd/dvd
usb hdd


tks

nals

---

### Post by nals on 2014-10-22
i installed debian wheezy as a second OS after installing xubuntu 14 04, it installed grub in the mbr , thereafter when i turn on computer, it takes me to the 'old' grub menu, and i can boot xubuntu off that

as is working fine, i will stick to that modus operandi for now

tks for your help

nals

---

### Post by Bucky Ball on 2014-10-22
Please mark the thread as solved by following the second link in my signature. Good luck. ;)

---

