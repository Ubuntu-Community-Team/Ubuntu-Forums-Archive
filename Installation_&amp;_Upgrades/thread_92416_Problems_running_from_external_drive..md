---
title: "Problems running from external drive."
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by JHawk24821 on 2005-11-19
After reading "[SUCCESS - Breezy loaded on external USB drive !]("http://www.ubuntuforums.org/showthread.php?t=80811&highlight=USB+hard+drive")" by DaBruGo (well written and very helpful by the way!), I decided to give it a try. Everything went well until I tried to boot the newly installed OS for the first time.

For those familiar with the thread linked above, I made necessary changes:

[LIST]
[*]GRUB installed only on /dev/sdc
[*]Edited /etc/mkinitramfs/modules as instructed
[*]Added 'WAIT=12' to the top of /etc/mkinitramfs/initramfs.conf
[*]Ran "mkinitramfs -o /boot/initrd.img-2.6.12-9-amd64-generic /lib/modules/2.6.12-9-amd64-generic"
[*]Edited /boot/grub/menu.lst, replacing hd4 with hd0[/LIST]
I have numberous devices hooked up to my machine, and this is my 'daily driver' running Windows XP. Here is the hardware breakdown just in case it's useful in troubleshooting:

[LIST]
[*]AMD 64 3500+
[*]ASUS A8N-SLI Premium with both onboard RAID controllers enabled (one is empty)
[*]nVidia 7800 GT 256 MB
[*]Primary Windows hard drive: 74 GB WD Raptor on one of the RAID controllers.
[+]Second Windows hard drive: 160 GB EIDE on IDE 1 master
[+]Third Windows hard drive: 250 GB EIDE on IDE 1 slave
[+]Fourth Windows external USB hard drive: 200 GB IDE
[+]Ubuntu external USB hard drive: 40 GB IDE
[*]Pioneer DVR-109 on IDE 2 master
[*]Plextor PX-W4824A on IDE 2 slave
[*]40 GB Apple iPod on Firewire
[*]5 GB Seagate USB hard drive
[/LIST]

I used my motherboards built-in 'Boot Menu' to choose what drive to boot to, so there is no problem at all choosing what OS to start (Windows is default). When I choose to boot to the 40 GB Ubuntu hard drive, everything seems to run fine at first - it even makes it to the graphical splash screen saying 'Loading Modules...". After about 10 second or so, it kicks me out to this screen:

```
  Booting 'Ubuntu, kernel 2.6.12-9-amd64-generic Default '
kernel direct mapping tables upto ffff810100000000 @ 8000-c000
root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel  /bot/vmlinuz root=/dev/sdc1 ro quiet splash
   [Linux-bzImage, setup=0x1c00, size=0x13e30e]
initrd   /boot/initrd.img
   [Linux-initrd @ 0x3faf1000, ox4eebce bytes]
savedefault
boot
.
Decompressing Linux...done.
Booting the kernel.
Loading, please wait...
[   55.564579] sda: assuming drive cache: write though
[   55.566578] sda: assuming drive cache: write though
ALERT! /dev/sdc1 does not exist. Dropping to sell!
```

I am pretty new to *uix, so I am lost as far as what to do next. If I had to guess, this is the offending line:

```
kernel  /bot/vmlinuz root=/dev/sdc1 ro quiet splash
```

Seems I need to change /dev/sdc1 to read /dev/hd0, but I have no clue where to find that setting and change it.

Any help would be greatly appreciated, and thanks for taking the time to read thought this.

;)  Jesse

---

### Post by JHawk24821 on 2005-11-20
Anyone. . .

I would like to have this running by next week.

:???: -Jesse

---

### Post by JHawk24821 on 2005-11-21
:( Looks like no Ubuntu for me.

---

