---
title: "Please Help - Installed Lubuntu Now Screen Flickers and Won't Boot"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by Stvnx7 on 2013-04-16
Hi, 

I have using boot-repair from a lubuntu live cd. It didn't work. 

This is the output I got:

[http://paste.ubuntu.com/5714585/](http://paste.ubuntu.com/5714585/)

Please help. 

Thank you!

---

### Post by Stvnx7 on 2013-04-17
OK - so I didn't actually "fix" it but I was hoping this would help others that are having the same problem out.

When the screen continually flickers, I *think* the system is actually in a boot loop. 

What I did is press "ESC" continually during the boot loop, and eventually I get to a boot menu that lets me choose ubuntu. 

Then it works fine.

Again, it's not a fix - more of a workaround - but I hope that helps others on this board.

---

### Post by dino99 on 2013-04-17
boot-repair report "syslinux" instead grub-pc as the bootloader
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

