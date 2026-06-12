---
title: "Tried to Trpple Boot, now only get Error where GRUB should be"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by jr226 on 2010-07-30
Hi, I have an IBM T60 which already had Windows 7 and Ubuntu 10.04 running fine in dual boot.  For work reasons, I also needed Windows XP, so I started to install it last night.  The install didn't work because of lacking SATA drivers, but when I tried to reboot my computer, GRUB was giving an error. [grub rescue>]  Rebooted with the live CD and attempted to reinstall GRUB, but I still get the same error when I restart.  I reinstalled GRUB with the directions from here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Any advice?  I really need to get this running again soon!

Thanks!

---

### Post by oldfred on 2010-07-30
To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Understand with multiple windows installs only the first windows with the boot flag will boot from grub and then in windows you have to choose which windows to boot:

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

