---
title: "Need Help With Install"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by Mike.42 on 2008-04-13
I believe this is a perfect storm for install problems. I installed Fedora Core 7 on a laptop my aunt gave me. (it was running 2000 very slowly). The fedora install was tricky because I could not change the boot order in the bios because it has an admin password set by dell. Because the hdd was before the disk drive, I just pulled out the HDD to trick the bios to boot to a cd. This worked fine for fedora. I am now trying to switch to Ubuntu. For my Ubuntu install I do the same trick, the bios says booting to cd, i quickly replace the hdd. During the install, Ubuntu says it cannot detect the HDD. I have no way to change the boot order. Does anyone have any ideas?

---

### Post by diablo75 on 2008-04-13
You might have to take that damn thing apart and pull the CMOS battery (there may even be more than one in there) so you can clear that password.  You might also try hitting F10, or F11 or F12 or Del during POST.  This (on some machines) will bring up a alternate boot device menu, which you can select CD-ROM from...

Good luck!

P.S.

Don't ever pull or insert a IDE hard drive while the laptop is powered on.  You could ruin the logic board on the bottom of it, and never be able to access your data after that.  IDE devices are not hot-swappable.

---

### Post by Mike.42 on 2008-04-13
Thanks, but the only way to select the CD-ROM during post is to have the hdd removed. I have done allot of googleing on dell latitude laptops and everyone has said that removable of cmos battery does not work. On thing I just noticed is that the floppy drive is first on the boot order. Is there any way to exploit this?

---

### Post by warp99 on 2008-04-13
You can boot to a floppy using Gujin bootloader then to the LiveCD:

[http://sourceforge.net/project/showfiles.php?group_id=15465](http://sourceforge.net/project/showfiles.php?group_id=15465)

> Quick method to install Gujin to a floppy

Download the install-x.x.tar.gz file from sourceforge.

Extract the boot.144 file.

Copy the above file to a floppy disc via the below command:

Code:

cat boot.144 > /dev/fd0

Floppy disks are one of the least reliable media around, so be prepared for multiple bad disks. It's a good idea to compare (with cmp) the written floppy disk with the image file. If cmp finds a difference, throw that floppy away and try another one.

Code:

cmp boot.144 /dev/fd0


    * At the Gujin prompt select the required OS / LIVECD.

Courtesy of this thread:
[http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

---

### Post by koenn on 2008-04-13
The Debian installation manual describes how you can download (or copy from a CD) the installer files to an exising system (eg your fedora), and then use that fedora's grub to boot the debian installer (from the hard disk)
[http://www.debian.org/releases/stable/i386/ch05s01.html.en#boot-initrd](http://www.debian.org/releases/stable/i386/ch05s01.html.en#boot-initrd)

---

### Post by koenn on 2008-04-13
> **Mike.42 said:**
>  floppy drive is first on the boot order. Is there any way to exploit this?

debian has "Smart Boot Manager" on its install cd's; they also let you boot of a floppy, then  use a CD.
[http://ubuntuforums.org/showthread.php?t=754245](http://ubuntuforums.org/showthread.php?t=754245)

---

### Post by Mike.42 on 2008-04-13
There is no floppy drive...I feel pretty dumb for not checking...

---

### Post by Pumalite on 2008-04-13
Have you considered?:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

