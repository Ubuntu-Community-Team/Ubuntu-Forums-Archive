---
title: "upgrading to ubuntu 12.04"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by micronet on 2012-05-01
hi

I'm unable to use my tv-out since ubuntu 10.10 and i'm sick of being obliged to move to windows whenever i want to use my tv as a monitor. To overcome this problem i tried to upgrade from 10.10 to 12.04 rather than installing directly the new version. I tried these steps to do so :

1- install a minimal command line system (10.10) from the minimal iso
2- sudo apt-get install xorg (to install xorg)
3- echo "xserver-xorg-video-intel hold" | sudo dpkg --set-selections (to hold this version of driver)
4- edit /etc/apt/sources.list by changing maverick by precise
5- sudo update
6- sudo upgrade
7- sudo apt-get install ubuntu-desktop


But sadly, this fails. 
I think my idea is clear. i want to have the newer version of ubuntu with the intel video driver found in 10.10 so i can get my tv-out working again. i have to say that the first six steps were executed successfully. The problems begin by installing the ubuntu-desktop meta package.

Any better idea ?
Please help me
thanks

---

### Post by micronet on 2012-05-02
is it impossible ???

---

### Post by kc1di on 2012-05-02
I no expert at video but I believe the problem your running into has to do with changes in new versions of how xorg is done.

In 10.10 Xorg was seperate from kernel now most video drivers are included in the kernel.  so I think what your trying to do is possible but you may not be able to use anything above the 2.6.x kernel to do it. that's why when you install ubuntu-desktop it fails because it upgrades to the 3.2 kernel. 

With all that being said tells what video card your using , what type of output to the tv IE HDMI or other ?

---

### Post by micronet on 2012-05-02
thanks for your reply

My video card is an integrated intel chipset (965)
my tv-out is a s-video one (not HDMI)

---

### Post by micronet on 2012-05-03
no hope ???

---

### Post by mips on 2012-05-03
> **micronet said:**
> no hope ???

I doubt it. jumping 3 versions and retaining a old package does not seem feasible. Best to do a fresh install and try and fix whatever issue you have with the video out.

---

### Post by darkwolfalone on 2012-06-20
I have the exact same problem. I can't get TV-Out after upgrading from 10.10 either. And not a single person in chat or the forums has seemed to come up with a solution to this problem. Super frustrating.

---

### Post by darkwolfalone on 2012-06-20
I have the exact same problem. I can't get TV-Out after upgrading from 10.10 either. And not a single person in chat or the forums has seemed to come up with a solution to this problem. Super frustrating.

I am also using an Integrated Intel chipset and S-Video.

---

