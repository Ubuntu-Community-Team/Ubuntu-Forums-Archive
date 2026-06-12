---
title: "Unable to boot into Windows after installing ubuntu"
date: 2005-03-25
forum: Installation &amp; Upgrades
---

### Post by DaturaX on 2005-03-25
After installing ubuntu, I'm able to boot into it flawlessly but when I try booting into my windows using grub as the bootloader, it gives me this error.

root (hd2,0)
Filesystem type unknown, partition type 0x7
Savedefault
makeacitve
chainloader +1

I've tried setting the HDD to LBA or large in CMOS but to no avail.

Tried using the WindowsXP CD and boot into recovery console, type fixmbr and fixboot but when I reboot, I get this error message.

Unable to load operating system.

What do I do, I am at my wits ends. 

here's my grub.conf

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,6)
kernel		/boot/memtest86+.bin

title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

edit:

I tried replacing ntdetect.com and ntldr as mentioned in one of the HOWTO but still to no avail. Anyone else has a fix on this? I need to use windoze for work..  :cry:

---

### Post by Jad on 2005-03-25
You know what, you are lucky!
anyway if you insist to get into windows 
check [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Kimm on 2005-03-26
> 
Tried using the WindowsXP CD and boot into recovery console, type fixmbr and fixboot but when I reboot, I get this error message.

**Unable to load operating system.**


I got that very same error message once (it was exactly the same even), I was unable to get windows to work again! I reinstalled it, different versions of it, like 5 times, but no change... This never happend when I was intalling ubuntu, it was when I was installing Slackware a while back, linux still booted perfectly from the the hdd however. Ofcourse if you change the hdd you can install windows on that. I'm afraid you have a Linux only computer now ;-)

---

### Post by MetalMusicAddict on 2005-03-26
Anyone with this problem set the access mode to the HD in your BIOS to "LBA" (Large Block Addressing) instead of "Auto". I had the same problem.

---

