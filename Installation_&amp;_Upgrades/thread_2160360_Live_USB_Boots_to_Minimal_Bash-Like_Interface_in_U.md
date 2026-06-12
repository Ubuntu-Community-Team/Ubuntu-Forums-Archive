---
title: "Live USB Boots to Minimal Bash-Like Interface in UEFI Mode"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by Shabamrei on 2013-07-06
Hi,

I have an Acer Aspire V5 laptop that came with Windows 8 installed. I've been trying to set up a dual boot with Ubuntu. I made live flash drive with Ubuntu 13.10. However, when I boot from it, I end up in this minimal bash-like interface grub command prompt. The drive boots in Legacy Bios mode just fine, but not in UEFI mode. I have disabled fastboot, and I don't think my laptop has SRT. Any suggestions? 
Thanks very much.

---

### Post by oldfred on 2013-07-09
When booting in UEFI mode, you do get the grub menu. But may need boot options and you have to manually add them to the linux line. Use e at grub menu, scroll down to linux line and replace quiet splash with nomodeset. Other or several in combination boot parameters may be required. What video chip do you have or is it dual video?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Shabamrei on 2013-07-10
Thanks, but I actually resolved the issue. It turns out that the program I was using to make the flash driver, Universal USB Installer, was not partitioning the USB drive correctly.

---

