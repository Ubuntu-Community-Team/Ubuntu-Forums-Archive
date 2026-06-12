---
title: "Linuxant installation and Belkin Wireless PCI"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by raistrick on 2005-02-02
Hi, i'm a uni student, trying to get the hang of linux - but having some trouble getting off the ground - few issues

firstly my system info:
Belkin Wireless card PCI
AthalonXP 2Gz
Nforce Chipset
GeForce Graphics card
(think thats all you need to know)
Fresh install of Ubuntu

Getting internet - after looking on here it seems that the best way was to install linuxant and then install windows drivers to get my Belkin Wireless card activated... so i went to the site

i have 3 files:
- dldrinstall.run
- driverloader-2.24.tar.gz
- driverloader_2.24_i386.deb

clicking on the deb file gave me an error saying it couldnt open so i ditched that

i ran the dldrinstall... that came back opening up mozilla, which was then asking for a username and password i knew nothing about

so i unziped the tar file and installed that, all went swimmingly until i got to calling dldrconfig... this then asked me to verify where my kernel was and showed me [/usr/src/linux] to which i obviously just pressed enter and up comes some error saying not found.

can anyone tell me where i am going wrong and maybe tailor the linuxant installation procedure for ubuntu

i was logged on as root by doing "sudo su " followed by the password i gave my first username on ubuntu install. after trawling the site i assume this is the only (or best) way to achieve root permissions

many thanks to all who reply!

---

### Post by sunscape on 2005-02-02
Skip the linuxant drivers and just use ndiswrapper. It is more or less simple to use and it is free. 

Download the windows drivers for your wireless card and use ndiswrapper to make it work. You can find guides through google that are simple to follow.

---

