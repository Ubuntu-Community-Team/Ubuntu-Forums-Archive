---
title: "Cannot install any video driver 14.04"
date: 2015-11-01
forum: Installation &amp; Upgrades
---

### Post by troopersec442 on 2015-11-01
Hey guys (and gals),
I'm relatively new to Ubuntu. I was trying to install the proprietary Nvidia binary using the guide from 
[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/) 
to no avail, and now I tried 
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
 also to no avail. The output I get after doing sudo service lightdm stop and running the nvidia .run from there is "failed to load NVIDIA kernel". Now im stuck in the 640X800 res and I cannot seem to get nouveau to work again either. I'm at wits end. I've been prowling the forum all day looking for a fix for me. I really REALLY don't want to reinstall OS again (there were issues with the first few installs).

---

### Post by Vladlenin5000 on 2015-11-01
Hi and welcome.

Please inform what Ubuntu version have you installed and what hardware you have (Nvidia graphcis card/chip). Meanwhile stop what you're doing because you're making things worse.

---

### Post by troopersec442 on 2015-11-01
14.04 LTS with a Geforce 560m

---

### Post by Vladlenin5000 on 2015-11-01
> **troopersec442 said:**
> 14.04 LTS with a Geforce 560m

As usual, you just go to system settings > Software & Updates  and find the rightmost tab Additional Drivers; wait a few seconds and you'll be presented with several options; select the recommended proprietary driver from the list, apply, reboot. DONE!
However, considering you already messed with things you shouldn't I suggest you first remove any trace of nvidia drivers that may have eventually been installed during such experiments. So, before anything else, open a terminal and do: 
```
sudo apt-get purge nvidia*
```
Reboot and follow the procedure above.

---

### Post by grahammechanical on 2015-11-01
+1

to the advice given by Vladlenin5000. But you do not say which Nvida driver you are trying to install. The Nvidia web site offers 352.55 for your video adapter. And if you have Ubuntu 14.04.3 you should see it in Additional Drivers which is the preferred method of installing proprietary video drivers in Ubuntu because the kernel team do some fixing so that driver installation does not get that "failed to build" error message.

By the way, Ubuntu makes installing video drivers very easy for those new to Ubuntu. As part of the installation process we tick the box labelled "install third party software" and some proprietary audio and visual codecs are installed as well as a proprietary video driver.

Regards.

---

### Post by troopersec442 on 2015-11-01
> **Vladlenin5000 said:**
> As usual, you just go to system settings > Software & Updates  and find the rightmost tab Additional Drivers; wait a few seconds and you'll be presented with several options; select the recommended proprietary driver from the list, apply, reboot. DONE!
However, considering you already messed with things you shouldn't I suggest you first remove any trace of nvidia drivers that may have eventually been installed during such experiments. So, before anything else, open a terminal and do: 
```
sudo apt-get purge nvidia*
```
Reboot and follow the procedure above.


This worked, Thank you. I suppose my next question is that if this is (clearly) the easy way, why does a google search for the process of using the proprietary drivers turn up a whole mess of "go into terminal and download this, erase that, move to this directory and sacrifice a goat"?

---

### Post by troopersec442 on 2015-11-01
> **grahammechanical said:**
> +1

to the advice given by Vladlenin5000. But you do not say which Nvida driver you are trying to install. The Nvidia web site offers 352.55 for your video adapter. And if you have Ubuntu 14.04.3 you should see it in Additional Drivers which is the preferred method of installing proprietary video drivers in Ubuntu because the kernel team do some fixing so that driver installation does not get that "failed to build" error message.

By the way, Ubuntu makes installing video drivers very easy for those new to Ubuntu. As part of the installation process we tick the box labelled "install third party software" and some proprietary audio and visual codecs are installed as well as a proprietary video driver.

Regards.

I ended up using the v346.96 proprietary tested.

---

### Post by Vladlenin5000 on 2015-11-01
There are a couple of reasons...

1. Users following the recommended and by far the easiest method as you noticed, rarely if ever go out of their way to post about a successful installation. why would they?
2. It often depends on the search you do, i.e., what some call "Google-Fu". Of course, the typical search expressions we think of will result in the most visited pages containing such expression and those are usually of discussions about what to do when something goes wrong with the preferred method, special cases or very new hardware for which the offered driver version isn't recommended* or doesn't work* at all.

* In such cases adding a third party repository (PPA) containing newer versions is still preferred. Using the installer from nvidia should be the last option.

---

### Post by troopersec442 on 2015-11-01
> **Vladlenin5000 said:**
> There are a couple of reasons...

1. Users following the recommended and by far the easiest method as you noticed, rarely if ever go out of their way to post about a successful installation. why would they?
2. It often depends on the search you do, i.e., what some call "Google-Fu". Of course, the typical search expressions we think of will result in the most visited pages containing such expression and those are usually of discussions about what to do when something goes wrong with the preferred method, special cases or very new hardware for which the offered driver version isn't recommended* or doesn't work* at all.

* In such cases adding a third party repository (PPA) containing newer versions is still preferred. Using the installer from nvidia should be the last option.

I see. Well my limited understanding of the OS has likely hampered my "google-fu" keywords. I would think the preferred method would be the first one to pop up. Regardless, thank you for helping the newbie Ubuntu user in his fumbling.

---

