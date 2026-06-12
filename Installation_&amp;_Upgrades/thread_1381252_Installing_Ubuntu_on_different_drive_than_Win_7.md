---
title: "Installing Ubuntu on different drive than Win 7"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by gilch on 2010-01-14
I have installed Windows 7 on one drive (300gb).
I have another 300gb drive available on which I want to install ubuntu 9.10.

There are many dual boot things on google but I can't figure out which would work for me. Some say they work for 9.04 but not for 9.10. Do some of you know a good tutorial for me?

Should I unplug the Win drive, and then install Ubuntu? If I do so I am not sure I can deal with the Grub thing.

Gilles

---

### Post by darkod on 2010-01-14
I wouldn't unplug anything. Grub2 needs to know about your win7 so it can create the boot option in the menu.
There really isn't much to it. What I would do:
1. Go into BIOS and set the drive dedicated for ubuntu to be first in hdd boot order. As a device list, the CD should stay before HDD.
2. Boot with ubuntu cd, Install Ubuntu option, and in step 4 tell it to Erase and use whole disk, selecting the disk you want in the drop down list. This is unless you plan to set up your partition for ubuntu manually. In this step remember what your ubuntu drive is called, probably /dev/sdb.
3. In the last screen, before clicking Install, click on Advanced and make sure the bootloader (grub2) will be installed on the same disk, /dev/sdb, if it was called like that. With multiple drives it is always good practice to check where the bootloader would go, to avoid surprises.

And that's it.
Grub2 will be on the ubuntu disk, and you already set it as first option to boot from, so you will select ubuntu or win7 from there. If by any chance grub2 is messed up and you need win7 urgently, changing the drive order in BIOS will boot win7 with no problem because we didn't touch the windows bootloader on that disk.

If you feel more comfortable looking at screenshots first, here they are for 9.10:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

