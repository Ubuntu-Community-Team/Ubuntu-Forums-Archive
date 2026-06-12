---
title: "getting Ubuntu to work on Libretto u100 mini laptop"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by gwledig on 2010-08-26
Hi
I spent a few days trying to get past grub errors when installing Ubuntu on a libretto u100 mini laptop so I thought I'd post how I got it to work (I'm not sure why it works but it does..)
 
Installing ubuntu 10 from CD didnt even get to the loading screen I had a whiring HDD and black screen.
 
Iniitally I found I could install Ubuntu 8 on the laptop but had to boot from the live CD, other wise I got a grub error.
 
I tried zillions of solutions suggested on the internet, to reinstall grub and use lilo but couldnt get any of these to work.
 
I tried upgrading Ubuntu to the latest (10) release but now found when I rebooted after serveral upgrades, that it never got past boot again, even when booting from the CD, I just got a blank screen and hard drive whiring like mad (as described on another libretto here: [http://sebjective.pronoia.biz/?p=23](http://sebjective.pronoia.biz/?p=23))
 
Finally I mamaged to install Ubuntu by installing Kbuntu, which allowed me to get to the install screen, but crashed after selecting 'install' (with a wierd corrupted logo on screen suggesting a graphics issue) I got around this by using F6 and adding xforcevesa in the boot option as described in the URL above, to force use of Vesa drivers. 
 
After installing Kbuntu I found it would also boot using grub without having to boot from the live CD. 
 
Then I used some code to install gnome desktop, it rebooted into gnome and so I now have the gnome style interface (admittedly with all the kbuntu stuff lying around). But it works fine.
 
 
So this is a solution to quickly get working on libretto, just use kbuntu with the vesa command, then install gnome desktop from inside kbuntu.
 
I think I used this page to change over to gnome [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)
 
If anyone knows of a simple way to just install the latest release of Ubuntu on a libretto u100 id be pleased to hear it instead of the above workaround.

---

