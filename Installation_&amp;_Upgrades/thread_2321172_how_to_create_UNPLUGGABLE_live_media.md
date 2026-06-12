---
title: "how to create UNPLUGGABLE live media"
date: 2016-04-20
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2016-04-20
how to create UNPLUGGABLE live media?   by this i mean to unplug the USB flash media i booted from w/o any other media.  i do have 16GB RAM.

i want to do this with 14.04 and/or 16.04.

---

### Post by RobGoss on 2016-04-21
I'm not sure I understand this question are you referring to a USB device?

You might have to give us a bit more of what your trying to accomplish here.

---

### Post by sudodus on 2016-04-21
Do you mean that you want to run Ubuntu in RAM?

And easy way is to use the boot option **toram**.

There is a tutorial thread about a more advanced system: [Making Ubuntu Fast using RAM (updated and simplified)](http://ubuntuforums.org/showthread.php?t=1594694)

---

### Post by Skaperen on 2016-04-22
i was hoping the tool to build the live media had a way to do this as it built it.  i have a bunch of 8 GB USB flash drives.  it's not about making it faster (caching does a decent job); it's about booting up N machines with X flash drives, when X < N.

---

### Post by sudodus on 2016-04-22
You can try with a persistent live drive booting via grub2 , and edit the boot option toram into **grub.cfg**.

***Edit:*** Boot it 'live-only' (don't select the persistent option), so edit the correct menuentry, maybe move it to the top position in the grub menu.

I tested with a persistent live Lubuntu 16.04 LTS made with [mkusb](https://help.ubuntu.com/community/mkusb/persistent). I edited grub.cfg, booted into RAM, unmounted the mounted partitions and unplugged the pendrive.

You can also remove the usbdata and casper-rw partitions and the menuentry for persistence. Then there will be no confusion or need to unmount anything. The ISO9660 partition is read-only, so it will not be damaged by unplugging, even if mounted.

After testing that it works like you want it to work, you can clone this pendrive to the other pendrives :-)

---

