---
title: "Booting Ubuntu with NTDLR"
date: 2006-05-25
forum: Installation &amp; Upgrades
---

### Post by DavidRanieri on 2006-05-25
I have a pc with three hard drives two sata one IDE.
sda has windows xp pro
sdb has ubuntu with grub boot loader
I used bootpart.exe to change the windows boot loader when rebooting both windows and Linux shows up on the boot screen but when choosing Linux it will not boot. Can some one tell me what my mistake is. Please see my boot.ini file below:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\bootsect.lnx="Linux"

---

### Post by Randomskk on 2006-05-25
I would reconmend writing GRUB to the MBR and having that control booting both windows and linux. That way has always worked for me, and many other people.

Is there meant to be a space in between "WINDOW" and "S"? (under default).

Besides that I can't offer much advice, have you tried looking online for a guide to using NTLDR with linux?

---

### Post by DavidRanieri on 2006-05-25
Sorry but on two drives that is impossible windows will always boot first especially if they are sata and are both set to master. I do not want it to be slave to anything. That is why I am asking this in this way. Also wiping out the windows ntdlr to just run linux is more of a hassel. That space between 'WINDOW" and "S" is being put there by the forum post.

---

