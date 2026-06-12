---
title: "setting up lubuntu 13.04 x64 with a ram drive for system files"
date: 2013-07-14
forum: Installation &amp; Upgrades
---

### Post by shultzjr on 2013-07-14
hi all,

I just finished a standard install with lubuntu 13.04 x64 onto an E6500, 4G of ram and a 1T Hitachi sata2 7200 rpm hard drive.  sda1=4g swap, sda2=100g root and sda3=rest of drive.  I would like to set up my ram so that the last 1 or 2G is set up for a ram drive that has all the system files and the first 2 or 3G of ram is used as regular ram.  this should speed up the system a lot by getting around the slowness of the hard drive.  how do I do this?  the motherboard I have maxes out to 8G or ram but I don't want to spend that kind of money at this time and ssd's are out.  my current kernel size is less than 600K.  the biggest program i use seems to by chromium the browser.

thanks,
charles......

---

### Post by dino99 on 2013-07-15
zram is already used by Lubuntu
but note that with your 4Gb, you will see nothing better
[http://amjjawad.blogspot.fr/2013/06/zram-testing-reports.html](http://amjjawad.blogspot.fr/2013/06/zram-testing-reports.html)

---

