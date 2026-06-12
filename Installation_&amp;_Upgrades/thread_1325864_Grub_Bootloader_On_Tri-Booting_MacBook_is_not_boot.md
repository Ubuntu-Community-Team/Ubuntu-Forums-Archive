---
title: "Grub Bootloader On Tri-Booting MacBook is not booting properly"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Vorksholk on 2009-11-13
[SIZE="3"]Ok, so for a little while I have had a great Tr-Booting MacBook which runs Ubuntu 9.04, Mac OS X Snow Leopard 10.6.1, and Windows 7 Service Pack 0 I think. I first had Leopard Running, upgraded to SL, made a BootCamp partition, installed Vista, then installed Ubuntu, then Ubuntu had problems and I reinstalled, and I think I still have the corrupted installed version on some partition like 1s5 or something like that and then I upgraded to Windows 7, it got rid of the bootloader, and the I ran:

Sudo grub
find /boot/grub/stage1
root (hd0,6)
setup (hd0,6)
quit 
and the bootloader then worked again, and has been working up until today. Today, I booted the MacBook  up and held option. I then selected the Hard Drive "WINDOWS" as that is the partition that Windows 7 is loaded on in addition to Ubuntu, and Scrolled down to Windows Vista (what the BootLoader calls my WIndows 7 partition) and then it hung at 


GRUB __ with the ___ flashing.

I booted into my Ubuntu Live DVD, and ran

Sudo grub
find /boot/grub/stage1
root (hd 0,6)
setup(hd0,6)
quit
and after the first command, I knew something was wrong because it returned something along the lines of "GRUB" is not reconized as a command or something. Any ideas to what I can do as I have a few files on the Ubuntu Partition that I am a TAD worried about, though I might have them backed up. Is there any way to either recover my Bootloader that is GRUB, or at least access the file from my MAC OS X SNOW LEOPARD partition so I could possibly back up the files to my MacBook and then do a reinstall? HELP! :confused: ](*,)[/SIZE]

---

