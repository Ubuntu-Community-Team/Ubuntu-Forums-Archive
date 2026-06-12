---
title: "question about ubuntu"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by scandune on 2007-07-10
i ran the live cd and i clicked on the install button and it supposidly installed on my SATA drive but when i go to restart the computer it says error loading the o/s  i have tried this with both ubuntu and fedora core 

system specs
150 gig wd raptor x sata 10000rpm
250 gig wd sata 7200
100 gig wd ide 7200

intel p4 3.4 extreme edition processor

2 gig ram

256 mb radeon 9800 xt

i also have dual monitors can i use this or will they be mirrored?


i am thinking that its the grub manager that is misinstalled or is it because of the sata drives?

---

### Post by scandune on 2007-07-10
i am currently using win xp and not thrilled about it anymore

---

### Post by confused57 on 2007-07-10
Have you tried booting first to your IDE drive, grub's IPL may have been installed to it's mbr?

You might want to boot the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a small "L"

---

### Post by inuyokai on 2007-07-11
Did you have another OS installed on your IDE drive?

That happened to me when I installed Ubuntu on my SATA with my IDE plugged in that used to run Windows XP.

All I did to get it to work was unplug the IDE drive and reinstall. I'm now dual booting Ubuntu and Vista from my SATA drive. Then I plugged the IDE drive back in and havent had any problems. I'm not sure if this is an option for you or not, it just worked for me and was easy to do.

Cool thing is that my IDE drives are seen by Ubuntu and accessible.

---

