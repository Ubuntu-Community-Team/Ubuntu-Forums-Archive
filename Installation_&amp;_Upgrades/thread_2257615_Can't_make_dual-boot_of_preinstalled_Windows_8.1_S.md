---
title: "Can't make dual-boot of preinstalled Windows 8.1 Single Language and Ubuntu 14.04.1"
date: 2014-12-21
forum: Installation &amp; Upgrades
---

### Post by artyomgapchenko on 2014-12-21
Hello.
I have Acer ASpire vn7-591g-598f and today I tried to install Ubuntu onto it. I've done everything as described in [this article]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html"). In the end I run boot-repair as described [here]("https://help.ubuntu.com/community/Boot-Repair#Advanced_options"), it worked without any issues (the result can be found [here]("http://paste.ubuntu.com/9587873")), but when I restart my laptop, Windows is loaded w/o Grub menu appearing.
What did I do wrong?
Thanks in advance.

---

### Post by artyomgapchenko on 2014-12-21
Okay, the thing was that I had to run
[COLOR=#000000][FONT=Tahoma]bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi[/FONT][/COLOR] 
in PowerShell right after boot-repair finished its job. Now everything works just fine.

---

