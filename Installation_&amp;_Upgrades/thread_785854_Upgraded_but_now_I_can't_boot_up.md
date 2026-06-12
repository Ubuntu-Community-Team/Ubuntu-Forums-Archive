---
title: "Upgraded but now I can't boot up"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Stoodle on 2008-05-07
Hi guys! I was upgrading to ubuntu 8.04 (that's what it is now right?) and everything was going fine. However, the updating process was going to take a while so I left it on over night. However, when I came home, I found that my computer was turned off. I was told that my uncle was probably using it during the day so I figure he just casually turned it off and then did whatever. My problem is that it appears that my home folder was deleted and a lot of commands can't be found such as w3m, sudo (how does it lose sudo?), apt-get, aptitude, and so on. Luckily, I backed up my home folder before I did this but still. I don't know how to redo the install since nothing's working. I don't get a splash. It freezes after saying the it's running local boot scripts or something.

Help!

:confused:

---

### Post by briandu on 2008-05-07
More info is required.
what pc - laptop - size - video card - cpu - memory etc. It helps.

assuming you take a live disk then bot up into live disk to check out hard drive.

---

### Post by Stoodle on 2008-05-07
I have a Compaq Presario with 512 RAM, 80 GB HD, 2.14(?) AMD processor, and ProSavage video card. 

To see what I had on my hard drive, I chose recovery mode and put in my root password. Then I used the terminal to try to see what I had. Home folder wasn't there, and I typed sudo apt-get upgrade and it said sudo:command not found. i did apt-get and got apt-get:command not found, and so on.

---

### Post by Stoodle on 2008-05-08
My other problem is now that I'm trying to reinstall, I can't do it! I tried to get the computer to read from the cd drive and it won't. It just goes to grub. Whenever I go to recovery mode and try to shutdown or reboot, it gets stuck at "Saving the system clock".

Apparently, shutting down a computer while it's updating can make life inconvenient.

---

