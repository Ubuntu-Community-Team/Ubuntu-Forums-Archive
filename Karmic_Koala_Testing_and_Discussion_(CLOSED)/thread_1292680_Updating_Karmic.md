---
title: "Updating Karmic"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Shady3D on 2009-10-16
hi everyone,

problem:
when installed Ubuntu Beta version from the Ubuntu website and worked well, but after i made the system update Ubuntu doesn't load x-server it goes to tt1-tt6 and wait for user logging in tt1.

i checked for upgrades to make sure nothing is left and rebooted again, but the same problem occurs.
i tried to access Linux kernel .11 instead of accessing Linux kernel .14 but the same problem happens.

my specs:
i'm using Ubuntu karmic x64, intel Pentium D, nvidia GeForce 9400 GT

---

### Post by VMC on 2009-10-16
> **Shady3D said:**
> hi everyone,

problem:
when installed Ubuntu Beta version from the Ubuntu website and worked well, but after i made the system update Ubuntu doesn't load x-server it goes to tt1-tt6 and wait for user logging in tt1.

i checked for upgrades to make sure nothing is left and rebooted again, but the same problem occurs.
i tried to access Linux kernel .11 instead of accessing Linux kernel .14 but the same problem happens.

my specs:
i'm using Ubuntu karmic x64, intel Pentium D, nvidia GeForce 9400 GT
Do you have the nVidia driver installed. Also if you have a xorg.conf file, remove it.

---

### Post by Shady3D on 2009-10-17
> **VMC said:**
> Do you have the nVidia driver installed. Also if you have a xorg.conf file, remove it.

can you explain more.

---

### Post by VMC on 2009-10-17
> **Shady3D said:**
> can you explain more.

Installing [nVida]("http://www.psychocats.net/ubuntu/nvidia") drivers.

Removing xorg.conf: rm /etc/X11/xorg.conf

The installing nvidia is self explanatory.

The reason for removing xorg.conf, is that this has meet with some success. It should be noted that usually you have to create that file in the beginning.

---

### Post by Shady3D on 2009-10-17
i installed the recommended nvidia driver and removed xorg.conf but the problem keeps on comming. i think its a problem with upstart because i noticed on my laptop (karmic 32 with intel CPU and GPU) the same sequence happens but it continues, but on my pc it stops.

[IMG 1]("http://picasaweb.google.com/lh/photo/bjo73fht4P5roQU7upV9RQ?feat=directlink")

[IMG 2]("http://picasaweb.google.com/lh/photo/FVSh5QNXHyQ4uoYkM73QZw?feat=directlink")

---

### Post by VMC on 2009-10-17
Has your gdm been removed somehow?
```
aptitude show gdm
```

---

### Post by Shady3D on 2009-10-17
i checked for gdm and it exist, also tried to install it again to see if there are any dependencies needed, but every thing is fine and the same problem exist.

---

### Post by VMC on 2009-10-17
OK next. Can you output both .xsession-errors & .xsession-errors.old from your home dir.

---

### Post by todak on 2009-10-17
When you are at the login screen, press **Alt+F7** to get to the graphical login. You may have to continue doing so each time you boot the computer until later updates come along. I had the same problem a few weeks ago, but after updating, the problem went away.

---

### Post by Shady3D on 2009-10-18
> **todak said:**
> When you are at the login screen, press **Alt+F7** to get to the graphical login. You may have to continue doing so each time you boot the computer until later updates come along. I had the same problem a few weeks ago, but after updating, the problem went away.

sorry but I've already tried this before. ALT F1 - F6 works but ALT F7 doesn't.

i'm starting to think its a curse.

---

### Post by Kareeser on 2009-10-18
How **exactly** did you install your nVidia drivers?

Be specific. I don't want to hear "I installed them correctly". Tell me how.

I'm guessing the driver needs to be recompiled because you downloaded a new kernel revision.

---

### Post by Shady3D on 2009-10-18
> 
How exactly did you install your nVidia drivers?
Be specific. I don't want to hear "I installed them correctly". Tell me how.
I'm guessing the driver needs to be recompiled because you downloaded a new kernel revision.


first time i installed nvidia there was a GUI, so i installed it using the restricted hardware application, it worked fine till i updated, some crash happens in the middle then i opened again to continue updating the GUI still was working.

after having this problem i thought of installing nvidia again so i removed nvidia-173-mod... nvidia-185-kernel-source nvidia-185-libvdpan nvidia-185-mod... nvidia-96-mod... nvidia-common nvidia-glx-185 nvidia-settings -dkms

after removing all this i installed nvidia-185-kernel-source nvidia-185-libvdpan nvidia-185-mod... nvidia-glx-185 nvidia-settings -dkms (did this using sudo apt-get install nvidia-185-*), NOTHING CHANGES

i removed 185 again and installed nvidia 173 then 96 but nothing happened.

so i removed everything and installed what i removed in the first place so every thing is back in its place. and thats my story with Karmic and Nvidia

---

### Post by fedexnman on 2009-10-18
i hope ubuntu 9.10 ditches the 185 driver, i have a 9800 gtx and am having nothing but problems with the 185 driver, wont boot after install, the 173 driver works, but it seems like 9.04 ran smoother ?? i know 9.10 is still beta, n looks nice, but im still liking 9.04 better!!:confused:

---

### Post by Shady3D on 2009-10-19
> **fedexnman said:**
> i hope ubuntu 9.10 ditches the 185 driver, i have a 9800 gtx and am having nothing but problems with the 185 driver, wont boot after install, the 173 driver works, but it seems like 9.04 ran smoother ?? i know 9.10 is still beta, n looks nice, but im still liking 9.04 better!!:confused:

so you hate 9.10 because of the drivers?

---

