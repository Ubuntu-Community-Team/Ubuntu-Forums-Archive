---
title: "Issues installing Xubuntu &quot;Monitor out of range&quot;"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by enzo_ven_arg on 2009-11-14
Hey guys, I've been using Xubuntu on my acer inspire one netbook for a few weeks now and I really liked it. So I decided to install it on my desktop PC. I made a 20GB partition and then booted with my 8gb pendrive with a copy of Xubuntu on it (Used the same flash drive to install Xub on my netbook). So I got the booting screen, where you can choose wether to start "Live" in persistent mode or directly install, all gave me the same result after loading files, when you're supposed to see the desktop or the install windows the monitor goes **"out of range", showing a black screen**. The only thing i can do is open a command line. I tried creating a /etc/X11/xorg.conf with display and monitor section, but this doesn't help because each time i reboot this file dissapears.
I would really like xubuntu on my desktop, so any help is greatly appreciated!

My PC specs are these:
* Intel E4300 Core 2 Duo
* Nvidia 8800 GTS
* Asus P5W-DH Deluxe
* 2 GB DDR2 Corsair memory
* 200GB SATA WD HD
* **LG FLATRON L1530S 15-inc LCD monitor.**

Thanks!

---

### Post by mikewhatever on 2009-11-14
Try pressing f4 at the boot menu and selecting Safe Graphics Mode. Hopefully it will let you install the system and once there, get the proprietary nvidia driver in place.

---

### Post by enzo_ven_arg on 2009-11-14
Thanks for answering. I tried this but unfortunately it didn't work :(. I really don't know why am I having this problem, maybe my monitor is too crappy? I tried pressing F4 in the boot screen when you can select if you want to boot "live", persistent mode or install and nothing. I Selected live mode and when my screen blacked out pressed F4 and nothing. Tried the same selecting install and nothing... Today i used my usb linuxlive drive on a friends notebook and it worked fine, so it's not the flash drive. Any other suggestions?

Thanks a lot!!

---

### Post by mikewhatever on 2009-11-16
I think the problem is a combination of boot options and you hardware. Have you tried the safe graphics mode? You could also try to specify framebuffer resolution, by adding vga=xxx to the end of the boot line. I don't know the exact parameter for your hardware, but vga-771 may work, and if not, try another one from the link below.
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

---

### Post by pip010 on 2010-12-28
same issue gere. houever i tried on modern LCD HD screen and it says not supporter formatt.
I ma with nvdia fx5200 on intel p2 350mhz :D
and I have no lan/wifi on the system.

so my only guess is it didnt download nvdia drivers and it is using something WRONG! instead :)

and this F4 simply doesnt work.

any suggestions, maybe recovery with editing some file? xconf?

---

