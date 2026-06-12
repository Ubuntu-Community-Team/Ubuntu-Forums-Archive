---
title: "Burning nVidia drivers to cd"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by bw3249 on 2008-11-09
OK, through lots of trial an error I finally got umbuntu installed an working.  My hang up came when because for some reason I couldn't get my wired network adapter (I tried several) to work until AFTER I installed the restricted driver for my nVidia graphics card.  I got things working by borrowing a usb wireless adapter.  The wireless adapter was able to connect to a local free network and I could download and activate the restricted drivers.  As soon as I did that and rebooted, my wired network card started working.

I would now like to download and burn the nVidia drivers to a cd so that I can install them without a network, should I need to reinstall in the future.

I've downloaded the nvidia-glx-177_177.80-0ubuntu2_amd64.deb from the packages website.  It shows several related files.  Do I need to download them also?  If so, then do I need to download all files related to the related files?  Where does it end?  Is there an easier/better way to accomplish this?

Any assistance/advise would be appreciated.

---

### Post by logos34 on 2008-11-09
why not just use AptOnCD to backup ALL your deb pkgs (in /var/cache/apt/archives)--they may fit on a cd and and the nifty thing is it'll save you the trouble of downloading everything all over again!  That way you can rest assured all the dependencies for the nvidia driver are included.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by bw3249 on 2008-11-10
Cool!!!

I figured someone with more than my 2-days of experience with ubuntu would have a solution.

Thank you.

---

### Post by Chunky Dunk on 2008-11-10
> **logos34 said:**
> why not just use AptOnCD to backup ALL your deb pkgs (in /var/cache/apt/archives)--they may fit on a cd and and the nifty thing is it'll save you the trouble of downloading everything all over again!  That way you can rest assured all the dependencies for the nvidia driver are included.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

That's a great link... I wish I'd heard about it before!

---

