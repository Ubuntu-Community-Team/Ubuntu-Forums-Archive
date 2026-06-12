---
title: "Blank screen on boot hangs on recovery mode"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by sinoako on 2008-07-30
Hi after a fresh installation on windows xp i installed ubuntu 8.04.  

When i turn on my laptop there are 4 choices:
ubuntu 8.04
ubuntu 8.04 recovery mode
ubuntu 8.04 memtest
windows xp

when i select time first option the screen will just flicker and turn blank black

when i select recovery mode some text would show and would eventually hang with the last 6 lines ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]

when i select memtest it works

when i select windows xp it also works

need help please first time ubuntu user and first time tried to install ubuntu

------------
Now playing: [Moments Of Soul - Live My Life (Full Vocal Mix)](http://www.foxytunes.com/artist/moments+of+soul/track/live+my+life+(full+vocal+mix))
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by Pumalite on 2008-07-30
Boot your Live CD and post:
sudo fdisk -lu
Mount your pertinent partition and post /boot/grub/menu.lst

---

