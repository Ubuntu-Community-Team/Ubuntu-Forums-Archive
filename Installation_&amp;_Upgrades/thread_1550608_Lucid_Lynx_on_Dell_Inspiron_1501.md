---
title: "Lucid Lynx on Dell Inspiron 1501"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by spjackson on 2010-08-11
[COLOR=#000000][FONT=Arial]I have a 3 year old Dell Inspiron 1520 laptop  and I would really like to put Ubuntu 10.04 Desktop (AMD64) on it, but my attempts have failed.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]This laptop currently boots either Vista (32-bit) or Kubuntu 8.10 (AMD64). I have had Ubuntu of a similar vintage on it in the past. I want to keep this Kubuntu installation for the time being (because I have all my hardware working with it, including the internal wifi) and I want to install Ubuntu 10.04 on the empty 10GB partition that used to hold an old Ubuntu.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have downloaded the iso image and burned a CD. I have used this CD to install on a desktop machine, and have also booted from and run this CD on a Dell Inspiron 1521 as a Live CD, so I don&#8217;t think there&#8217;s anything wrong with the CD. If I boot my laptop from the hard disk&#8217;s Kubuntu 8.10 installation, then I can browse the CD without any errors, so I don&#8217;t think there&#8217;s an incompatibility issue between my optical drive and the CD.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]However, if I boot from the Ubuntu 10.04 CD, the initial almost blank screen with a logo at bottom centre of the screen is displayed, then after somewhat less than a minute, a screenful of vertical lines of multiple colours is shown, each line being between 1 and 5 pixels wide (estimated - photo available if it helps). This screen remains for a while until the CD stops being accessed, then eventually I give up and reboot. Booting from another CD containing 10.04 i386 Desktop has similar results.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Under Kubuntu 8.10, lspci shows my graphics card as:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]It works fine under Kubuntu 8.10 at 1280x800 (60.0 Hz).[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Any clues or suggestions for progress?[/FONT][/COLOR]

---

### Post by mörgæs on 2010-08-11
Is this problem similar to yours? 
[http://ubuntuforums.org/showthread.php?t=1475045](http://ubuntuforums.org/showthread.php?t=1475045)

If so, can you boot a 9.10 live CD?

---

### Post by Iowan on 2010-08-12
Fixed the title for you. ;)

---

### Post by spjackson on 2010-08-14
Yes, thanks very much for the link. That is indeed the same problem. 9.10 Live CD boots fine. I now have 10.04 amd64 working using the nomodeset boot parameter.

---

