---
title: "Karmic to Lucid : screen resolution"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by jcglt on 2010-04-29
On the 28th of April I upgraded my system (laptop with  "SIS Mirage 3 Graphics" video card) from Karmic to Lucid  and my screen resolution was reduced from 1024*768 to 800*600. I tried during one day to find the suitable driver but no luck on SIS web page. 

I eventually found it on the followwing address :
[http://dl.dropbox.com/u/983756/sis671_10.x.tar.gz](http://dl.dropbox.com/u/983756/sis671_10.x.tar.gz)

It works very well and the resolution has jumped now to 1280*800.
The only remaining and identified problem is with grub2 : my system is dual-boot (Windows XP and Ubuntu) and the "recovery" mode does not work anymore for ubuntu, I will maybe have to wait for a next update.

---

### Post by jcglt on 2010-04-30
Waiting for an improvement of my grub2 menu I found the following tentative solution to my second problem : I created a bootable USB key with "System" "Administration" "Start Disk Creator", which allows me to boot my PC on this USB key then edit any failing file.

---

### Post by jcglt on 2010-05-03
I have also discovered that since my upgrade to Lucid Lynx I cannot anymore open a console : the command CTRL+ALT+F1 to F6 leads to a "zebra" like screen and CTRL+ALT+F7 returns normally the computer to the graphic Gnome mode.
Well this explains why I cannot anymore boot in "recovery" mode where I get the same "zebra" screen and this is a nuisance as the recovery mode might be useful in some deteriorated situations.
Any thought about this non-functionning "console" mode ?

---

### Post by jcglt on 2010-06-01
SOLVED
I did the following :
- edit /etc/default/grug to read
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" quiet splash "
(comment I already had the first line BUT the second line ended in "quiet VGA=791" and the source of my problem was this VGA=XXX
- then in a terminal "sudo upgrade-grub2"
- reboot
Now I have a fully operative Ubuntu Lucid Lynx 10.04 with a working "recovery mode" start and when booted in graphic mode the ability to get six tty terminals by CTRL+ALT+F1 to 6 (return by ....... +F7).

---

