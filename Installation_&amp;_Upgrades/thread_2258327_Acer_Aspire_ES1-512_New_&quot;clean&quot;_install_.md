---
title: "Acer Aspire ES1-512 New &quot;clean&quot; install of ubuntu 14.04 - No bootable device found"
date: 2014-12-26
forum: Installation &amp; Upgrades
---

### Post by Ilgaisap on 2014-12-26
Hello,

I tried installing ubuntu 14.04 on my Acer Aspire ES1-512 over windows 8.1. I managed to install ubuntu without problems first, but then, after a reboot, the boot program does not find any bootable device.
I tried to look for answers on the web; the problems seems quite common with this computer. Altough I have tried to follow the answers on those topics (Everytime a new install to be sure), I could not solve my problem.
Therefore, I run boot-repair (see link at the end of the message).

Help would be greatly appriciated.
Thanks a lot in advance!

[http://paste.ubuntu.com/9626664/](http://paste.ubuntu.com/9626664/)

---

### Post by oldfred on 2014-12-26
You only have Ubuntu not dual boot.

You probably can just rename grub to be "Windows" in UEFI and have it work.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi"


 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)

---

### Post by Ilgaisap on 2014-12-27
Great, this solved my problem!
Thanks a lot for your help :-)

---

