---
title: "help with reinstallation of ubuntu 12.04"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by kevinorourke2008 on 2013-03-22
Hi Guys, I'm really happy with ubuntu 12.04 lts, except for the fact that mine is as slow as snail mail. My fault though as I haven't done a clean install since I wiped the dreaded windows off my Acer Aspire 1 some years ago, and since then I've only ever done upgrades.
My question to you is how do I do a clean install ?
I have an external dvd burner which works through the usb, and I know hot to direct the computer to boot from it. 
However, what I don't know how to do is format the hard drive and wipe the memory boot record ? So that the computer is bare ready for a new clean install !!
Any help will be greatfuly received.

Many thanks Kev.

---

### Post by ManamiVixen on 2013-03-22
You just install Ubuntu using a DVD/CD burnt/bought copy. Ubuntu formats and wiped the Hard Disk for you during the install. Just select "Use entire Hard Disk" for it to do that. Make sure you back up all data first to an external media whether it be a DVD or USB Stick before reinstall as the Hard Disk will be completely wiped.

---

### Post by kevinorourke2008 on 2013-03-22
thanks manamivixen, last time I did it I used a floppy disk to get the C/ prompt and then did fdisk/mbr "AAAAHHH I'm speaking windows crap again".
Ubuntu, so much easier.

Many thanks. Kev

---

### Post by oldfred on 2013-03-22
The default install is just / (root) and swap. If that is all you want then the auto install is the easiest way.

But if you want a separate /home or other partitions, control over sizes of partitions or other specific settings you have to use Something Else or manual install. You the create your own partitions, define format, specify mount (/, /home, etc) and where to install the boot loader.

       [URL="https://help.ubuntu.com/community/GraphicalInstall"]https://help.ubuntu.com/community/GraphicalInstall
[/URL]
 Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[URL="http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/"]http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/

      [/URL]
 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

I am afraid I remember the old DOS days, actually even CP/M. And with copy  order reversed in DOS messed up copies. :)

    [URL="http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/"]
[/URL]

[URL="https://help.ubuntu.com/community/GraphicalInstall"]
[/URL]

---

