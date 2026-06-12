---
title: "Ubuntu 14.04.02 installation with windows 8.1 : after Grub repair nothing boot"
date: 2015-07-30
forum: Installation &amp; Upgrades
---

### Post by glxagus on 2015-07-30
I have got a toshiba laptop Portege R930 -1h9 with windpws 8.1 installed.
I tried to use it, but I need a linux indeed.
Installed with live usb ubuntu 14.04.02.
After reboot it's started with windows.
I Tried some time the reboot, also from boot device options, but got no evidencef ubuntu.
Started a live usb ubuntu 14.04.02 and launched boot repair.
I did something and gave me 
[http://paste.ubuntu.com/11967396/](http://paste.ubuntu.com/11967396/)

I really tried to get in touch with windows 8 , but i couldn't. My limit.

Any suggestion ?

---

### Post by oldfred on 2015-07-30
Can you go into UEFI boot tab or one time boot key probalbly f12 with Toshiba and boot the ubuntu entry.

Toshiba has become like several other vendors that modify UEFI to only boot by description and only valid description is "Windows". That is not per UEFI standard.

Most copy shimx64.efi into /EFI/Boot. Backup bootx64.efi and rename shimx64.efi to bootx64.efi. The bootx64.efi is the fallback or hard drive boot entry and still works on those systems that only boot "Windows".

Details on copying in link in my signature.

       Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[URL="http://ubuntuforums.org/showthread.php?t=2267408"]http://ubuntuforums.org/showthread.php?t=2267408
[/URL]
 Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)

[URL="http://ubuntuforums.org/showthread.php?t=2267408"]
[/URL]

---

