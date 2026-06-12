---
title: "XServer Error while installing ATI driver"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by Anharath on 2008-11-08
Hi,
I downloaded an ATI driver for my graphicscard but when I run the command as root, I get an errormessage saying that my XServer is not installed (though I have installed it)
> root@yorik-desktop:/home/yorik/Desktop# cd sh ati-driver-installer-8.28.8.run
-bash: cd: sh: Bestand of map bestaat niet
root@yorik-desktop:/home/yorik/Desktop# sudo sh ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
_X Server: unable to detect_
Removing temporary directory: fglrx-install


I have also tried an .rpm file to run as root but I get an error message:
> root@yorik-desktop:/home/yorik/Desktop# sudo sh fglrx_6_8_0-8.28.8-1.i386.rpm
fglrx_6_8_0-8.28.8-1.i386.rpm: 1: &#65533;&#65533;&#65533;&#65533;fglrx_6_8_0-8.28.8-1&#65389;&#65533;P: not found
fglrx_6_8_0-8.28.8-1.i386.rpm: 1: y: not found
fglrx_6_8_0-8.28.8-1.i386.rpm: 1: 8&#65533;@&#65533;a
                                                        : not found
fglrx_6_8_0-8.28.8-1.i386.rpm: 1: b&#65533;: not found
fglrx_6_8_0-8.28.8-1.i386.rpm: 1: : not found
fglrx_6_8_0-8.28.8-1.i386.rpm: 1: : not found
fglrx_6_8_0-8.28.8-1.i386.rpm: 2: Syntax error: "|" unexpected
root@yorik-desktop:/home/yorik/Desktop# 


Can someone help me out? Perhaps I need to reinstall Xserver?
Thanks!
Anharath

---

### Post by Anharath on 2008-11-08
I reinstalled Xserver and still got the same problem..

---

