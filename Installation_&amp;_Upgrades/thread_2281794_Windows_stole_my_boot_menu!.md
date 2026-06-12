---
title: "Windows stole my boot menu!"
date: 2015-06-09
forum: Installation &amp; Upgrades
---

### Post by geekgirl2 on 2015-06-09
I've just spent the last week carefully setting up a dual boot situation with Windows 8.1 and Ubuntu15 on my HP laptop. It was supposed to be my big break from windows! (I left Windows 8.1 on the laptop in a dual-boot because it came with it installed already, and there is literally only one program I still have to use in Windows at the moment.)

I've been fighting with windows the whole time - watch out for the fastboot thing! - but it just recently took my boot menu away. I used to get the GRUB bootloader, and was able to select which OS, and go! But now, it just jumps to loading Windows :mad: It doesn't seem to matter if I hold down F8, DEL...although F2 gets me a useless (for my problem) diagnostic menu. The only thing I did in the interim, is I went into the BIOS to try and get the laptop to boot from a USB stick...that's it. And the boot options were already set fine; all I did is turn of "network boot" because I didn't need it.

How can I get my Ubuntu back!?

---

### Post by oldfred on 2015-06-09
Is Ubuntu booting in UEFI mode?
Almost all HP's have modified UEFI against UEFI standard to use destription to boot. And only valid description is "Windows". But hard drive entry works so we modify hard drive UEFI boot file bootx64.efi to really be grub or shim. Then you can boot hard drive in UEFI and get Ubuntu/grub.

       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
[/URL]
 sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

Also similar info in link in my signature.


[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

