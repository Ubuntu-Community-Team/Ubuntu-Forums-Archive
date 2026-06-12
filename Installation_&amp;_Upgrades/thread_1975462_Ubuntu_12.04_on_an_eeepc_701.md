---
title: "Ubuntu 12.04 on an eeepc 701"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by kgarbutt on 2012-05-07
A guy named Stuart over at this web site:

[http://gobitech.blogspot.com/2011/06/install-ubuntu-1104-on-asus-eee-pc-701.html](http://gobitech.blogspot.com/2011/06/install-ubuntu-1104-on-asus-eee-pc-701.html)

Posted how to get Ubuntu 12.04 onto an Eeepc 701 (it has a 4G SSD), and it is brilliant. Here is what he says:

Edit this file: /usr/lib/ubiquity/ubiquity/misc.py, line 796.

Replace this line: min_disk_size = size * 2
With this new line: min_disk_size = size * 1.4

Save the file and Ubuntu 12.04 will install. It is brilliant. Thanks Stuart. It also worked for Xubuntu 12.04 which I put on my Eeepc 701 this past weekend.

I just wanted to share his information.

Ken

---

### Post by smoka on 2012-05-13
Cheers kgarbutt, interesting to know, just about to go for a reinstall of mine with 12.04, been testing it on an SD card and must say quite like Unity now. I normally split off my /home directory onto a separate SD card as the 4GB is just too small for me.

---

### Post by joesnose on 2012-05-13
I have tried out 12.04 on my 701 but had problems with xrandr not scaling the screen properly, does anyone know if this is fixed or if there is a work around.

thanks.

---

