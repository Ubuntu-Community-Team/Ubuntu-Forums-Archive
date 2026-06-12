---
title: "HELP!!! I can't Install linux  black screen!!!"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by bfitz26 on 2012-03-15
**So here is my setup i have a 4 month old pc dual core 2.9 gighz. amd with built in hd graphics card 500 gig harddrive and a gigabyte motherboard. so i am trying install windows i need to use it for android things.. here is how it goes **

I boot from cd the first time. step my bios as cd as first boot device to avoid any issues. it boots says its installing counts down from 5 to 0 says it's installing. After that my screen goes black and nothing.Like i have no cable connected. I finally figured it out by pushing **f6** and **shift** saw it some where else changed **quitet splash to nomodset**  i got to the language packs to the point of where it says to reboot pc and now i does the black screen everytime. i am not understanding what is causing this and how to fix it!!! i am thinking about d.g. to ubuntu 10.x to see if that could be the issue but haven't tried yet..

---

### Post by 2F4U on 2012-03-15
Setting nomodeset through F6 in the liveCD is not carried over to the installed operating system. You need to change the configuration of the installed grub to get the setting back.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by bfitz26 on 2012-03-15
doesn't make sense this is my first time installing why do i get a freaking black screen after rebooting everytime ???!!!! don't understand why this is so complicated windows is a breeze!!

---

