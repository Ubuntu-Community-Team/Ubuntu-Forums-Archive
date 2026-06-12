---
title: "upgrade to 12.04 failing on boot up"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by djm on 2012-04-28
I have been running all vers of ubuntu on my laptop for the last 5 years with no problem. When i updadted to 12.04 on re boot I get the following on a black screen with a flashing cursor.

* stopping anac(h)ronistic cron
* stopping save kernal messages
*starting CUPS printing spool/server

*starting anac(h)ronistic cron

*stopping anac(h)ronistic cron

checking battery state....

*stopping system V runleval compatibility

some times I can get in a terminal by using ctrl/alt/f1

this happend wether i have the battery fitted or not

The update was done via the update manager and installed with out any failures 

laptop details
fujitsu siemans amilo
intel centrino
4gb ram
120g hhd

I would be grateful if anyone can throw any light on this fault cheers dave

---

### Post by dino99 on 2012-04-28
you might try some boot option like nomodeset or acpi=off

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by iponeverything on 2012-04-28
log in to a terminal and see if you have any useful debug info in the output of:

```
sudo dmesg
```

---

### Post by patricketurner on 2012-05-03
Just happened to me, won't go too far into detail on how lost I felt. My dad and I facetimed it and figured it out.

YOU WILL NEED AN ISO IMAGE OF A PREVIOUS UBUNTU VERSION (I USED 11.10)




Pop disk into computer as soon as it starts up. Hit F2 to go into boot manager screen. The boot section will ask where it wants you to load the OS. The first option is from the HDD. The third option should be from the CD. Select option 3.

Use F8 to move option 3 to option 1's space. Hit F10 to save and exit. 

Ubuntu 11.10 should boot from the CD. Once it boots it will ask you to install it on the harddrive, or keep using CD. Choose hard drive. It will later ask if you want to install it and keep saved files on computer. I tried this, and certain things like the mouse and wifi drivers did not install properly. I had to re-do it and do a complete fresh 11.10 install, saving nothing of my previous files.

I know this is not 12.04, but at least your computer has a working OS again after this. 

I am using a Toshiba Satelite A305D.

---

