---
title: "HOW TO INSTALL 12.04 on a machine with UEFI"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by perro68 on 2012-10-30
I just purchased a laptop with windows 8 and UEFI .. i Have a disc but when i boot the laptop does not see the disc ....I know the disc is good ..I can use it to boot other machines. I can use it to boot this machine if i change the bios to work with csm..but than of course i will not see my windows 8 partition

  How do i install ubuntu

PLEASE HELP!!!!!!!!!!

---

### Post by jerrrys on 2012-10-30
I really know nothing about UEFI, but I do know ..

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=UEFI&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=UEFI&as_qdr=all&sa=Google+Search&lang=en)

.. :)

---

### Post by oldfred on 2012-10-31
Since this is a new computer with preinstalled Windows 8, you are the first I have seen that probably has secure boot enabled. I have read some of the articles and discussion on how Ubuntu is going to handle that but I do not know. They are supposed to use the Windows key and be able to install with that. It may only be in grub2 2.0 which is in 12.10 and will be in 12.04 with the next point release in Jan.

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)
[http://www.muktware.com/4692/secureboot-ubuntu-1210#.UJCr7hIzDpE](http://www.muktware.com/4692/secureboot-ubuntu-1210#.UJCr7hIzDpE)

I think you can just turn secure boot off and then it is just a standard UEFI install. You do have to have the 64bit version.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

---

### Post by 8grod on 2012-10-31
Turn off Secure Boot in BIOS.

---

