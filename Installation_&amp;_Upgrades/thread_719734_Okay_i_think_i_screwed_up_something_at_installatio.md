---
title: "Okay i think i screwed up something at installation (dual boot related)"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by baqai on 2008-03-09
I installed ubuntu on my external usb drive a while back to give it a spin, being a newbie i made few mistakes which i am realizing now so following are few questions which needs to be addressed 

1. I had a installation of Windows Vista, boot menu does not show windows vista but shows old dumped Windows XP which actually works :o How can i boot to Windows Vista if i need to?

2. Right now i can only boot my computer with my external hdd attached, how can move the mbr (with fixed above problem) to external drive?

---

### Post by logos34 on 2008-03-09
> **baqai said:**
> how can move the mbr (with fixed above problem) to external drive?

[Reinstall grub to the MBR of the usb drive from the live cd]("http://ubuntuforums.org/showthread.php?t=224351").  Use 'setup (hd**1**)'.  Remember to edit **groot** and** root** lines in /boot/grub/menu.lst to (hd**0**,x).  (Because as soon as you change the bios to boot from the ubuntu usb it becomes hd0)

Restore vista bootloader to the internal hard disk.

Then toggle the Bios boot drive order for either windows or linux.

---

