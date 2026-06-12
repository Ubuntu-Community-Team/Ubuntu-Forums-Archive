---
title: "ubuntu 13.0 boot up darkness and nvidia video card"
date: 2013-11-22
forum: Installation &amp; Upgrades
---

### Post by ongandrew2 on 2013-11-22
hi good day to all my problem with ubuntu are:

1.) screen brightness = 0 whenever i startup even with the try ubuntu on cd the brightness is still 0
2.) can't reboot the computer when ever i shut down my computer it stays there and do nothing it says:
 the computer is going down for reboot now
acpid: exiting
speech-dispatcher disabled: edit /etc/default/speech-dispatcher

i have to manually hold the power button for it to shut down.
3.) the ubuntu app store always freezes and then resume then freeze again.

hope you could help me out with my encountered problems did search on google but didn't do any good.

My laptop is Acer V3 - 471G
Processor: Core i5 - 3210M
Display: GT630M 2 GB
RAM: 8 GB

---

### Post by oldfred on 2013-11-22
Do not use power button unless this does not work.
       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

have you installed the nVidia proprietary drivers? Or is your system dual video or Optimus?

If dual video & booting with Intel vide, you may need this as a boot option. You can test from grub menu like adding nomodeset.

 acpi_osi=Linux  acpi_backlight=vendor
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

