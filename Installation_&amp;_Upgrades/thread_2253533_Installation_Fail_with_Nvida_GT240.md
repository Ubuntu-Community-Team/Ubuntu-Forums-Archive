---
title: "Installation Fail with Nvida GT240"
date: 2014-11-20
forum: Installation &amp; Upgrades
---

### Post by jmberumenb2 on 2014-11-20
Hi 

My problem is every time I trie to install Ubuntu (no matter which one) now trying 14.04.1 LTS is failing at boot.

Only appears an static black screen full of artifacts this only happens on GT240 when I use the Internal Intel graphics everything is just fine...I don't wanna toss my card just for run Linux :(

[IMG][[IMG]http://imagizer.imageshack.us/v2/320x240q90/673/eG8l6d.jpg[/IMG]]("https://imageshack.com/i/ipeG8l6dj")[/IMG]

Can someone help me? Im a noob on this and trying to explore and get the most of ubuntu on my computer.

Any help will be appreciated.

---

### Post by oldfred on 2014-11-20
With my older nVidia card I always had to use nomodeset to boot installer and first boot after install or until I installed the nVidia driver from the System Settings.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
 Installer, if BIOS you press any key while tiny icons are at bottom of screen & then f6 to add nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by jmberumenb2 on 2014-11-21
> **oldfred said:**
> With my older nVidia card I always had to use nomodeset to boot installer and first boot after install or until I installed the nVidia driver from the System Settings.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
 Installer, if BIOS you press any key while tiny icons are at bottom of screen & then f6 to add nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Thanks a lot!!!!

Looks like this is an nvida-ubuntu combo problem but this fix my problems.!!! Thanks again!

---

