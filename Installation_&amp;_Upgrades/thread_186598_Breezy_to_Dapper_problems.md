---
title: "Breezy to Dapper problems"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by phlexy on 2006-06-02
Hey there.

I just installed Dapper today via terminal and I got no errors or anything.. though, when I restarted and got past the login screen I got nothing. Just a blank brown screen. 

Does anyone have any idea how I can fix this?

Any help is hugely appreciated. (By the way, I did use Search but I couldn't find anything that matched exactly this :P.)

---

### Post by barbarian on 2006-06-02
Hi,
Do you know exact specs of your video adapter? If so:

*ctr-alt-f1*
*sudo dpkg-reconfigure xserver-xorg*

answer to all questions, then try to reboot.
good luck

---

### Post by ubuntu_demon on 2006-06-02
Also make sure everything is installed properly.

Try to configure all packages that are unconfigured :
$ sudo dpkg --configure -a

Make sure everything is installed :
$sudo apt-get update
$sudo apt-get dist-upgrade
$sudo apt-get install ubuntu-base
$sudo apt-get install ubuntu-desktop (or kubuntu-desktop / edubuntu-desktop / xubuntu-desktop)

---

