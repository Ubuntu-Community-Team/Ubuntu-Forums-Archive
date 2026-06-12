---
title: "grub"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by cody7r on 2007-02-24
ok im fairly new to ubuntu actually just linux in general. but what i did was previously i had windows xp on my laptop then i decided to partition my hdd and put ubuntu 6.10 on the computer too. so i did that and now it loads up grub everytime i start the laptop up which is fine, i just want to know how to get rid of the memtest boot, i do not even know what it is for and i dont think i get into it enough for the recovery mode boot up either. well after i updated my ubuntu with security updates it now has 2 versions of ubuntu! so i have like 5 boot up options just for ubuntu, which i only want the normal boot of the most recent one, and if i could...get windows to be my primary boot up so when i turn it on and leave it it will automatically boot windows instead of ubuntu...

---

### Post by Gerard Barberi on 2007-02-24
I wouldn't recommend you do it...

gksudo gedit /boot/grub/menu.lst

in a terminal will pull up Grub's config file.  You can comment out any options you wish. (or you can also uncomment any, or also change the default OS)

---

### Post by cody7r on 2007-02-24
i know alot of people say that but is there a really big reason to not to, i mean i dont think i mess with the os enough to need to keep the other options, or is it not that stable??

---

