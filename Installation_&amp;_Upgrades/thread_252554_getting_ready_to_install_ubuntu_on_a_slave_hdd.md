---
title: "getting ready to install ubuntu on a slave hdd"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by slipk487 on 2006-09-07
im getting ready to but a new hdd and install ubuntu on the slave but i want to use windows 2k3 and my primary os and have ubuntu added to the boot.ini file and i dont know how to do that i check google and only thing i found was if ubuntu is on the same hdd and i didnt really understand it but i just need to know how to add it to the boot.ini if its the slave on the pirmary ide slot

---

### Post by aysiu on 2006-09-07
When you install Ubuntu, it'll install its own boot loader, which will automatically add Windows to the menu.

Automatic dual-boot set-up is much better than manual set-up. Trying to get Ubuntu into Windows' boot.ini is a lot more work.

Read more here:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by zxee on 2006-09-07
There are several howtos on editing the NTLDR (windows boot loader) [http://hacks.oreilly.com/pub/h/2337](http://hacks.oreilly.com/pub/h/2337) [http://www.highlandsun.com/hyc/linuxboot.html](http://www.highlandsun.com/hyc/linuxboot.html)
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/3443-dual-booting-windows.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/3443-dual-booting-windows.html)
Hope one of those is helpful.

---

