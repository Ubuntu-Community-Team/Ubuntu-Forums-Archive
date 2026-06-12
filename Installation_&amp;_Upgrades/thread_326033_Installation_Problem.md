---
title: "Installation Problem"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by Cobski on 2006-12-26
Hey, I'm new to Ubuntu, but I've tried other distros in the past. After recently installing 6.10 on a friends computer I was very impressed and decided to give it a go. The problem is, I can't get into the Live CD desktop environment on my machine. Here's what I'm working with:

AMD64 3400+
1GB Kingston HyperX
Nvidia 7800GT
Abit NF4 Motherboard

When I boot up the Live CD it loads fine, the orange/blue background pops up, the music plays, and I can move the cursor around freely. The problem is, that's all I can do, it doesn't go any farther. I've tried Ubuntu 6.10, 6.06, and Kubuntu 6.10 (all x86). I've tried both my DVD and CD drives - after it attempts to boot into the environment the drive light blinks for about a minute and then nothing. I've tried all the special boot parameters in the Live CD Help as well. I'm stumped, so I was hoping someone here knows what's up :-k . I'm DLing the alternate ISO now, maybe I'll be able to figure something out with that...

---

### Post by taurus on 2006-12-26
If you have the DVD version, try using the "alternate" one to install it on your machine...  And if you don't have the DVD version anymore, then download the alternate CD.

---

### Post by Cobski on 2006-12-27
Well, I installed Ubuntu with the text-based alternate CD, and everything went smoothly. When I booted it up, I got the same problem. I installed the newest Nvidia drivers through the command prompt. After the installation, using the telinit 3 command, I got the orange screen as well as the user account setup. I thought it was fixed, but after finishing the setup it wouldn't let me go past forward. I could click it, but it wouldn't do anything. Minimizing the window caused it to disappear into the lower right corner, so I figured it was a desktop environment problem. I tried Kubuntu 6.10 with the same results. I'm going to try reinstalling the OS and then reinstalling the drivers again, but I'm still very stumped ](*,) .

---

### Post by Cobski on 2006-12-28
Still no luck :-k .

---

### Post by Cobski on 2006-12-28
Problem solved, all I had to do was change my graphics driver to VESA in my xorg.conf :) .

---

### Post by riven0 on 2006-12-28
yeah, but you'll probably be disatisfied with the performance on vesa. My idea is to try [easyUbuntu]("http://easyubuntu.freecontrib.org/"); it'll automate the installation of your graphic drivers for you. 

Good luck! :KS

---

### Post by Cobski on 2006-12-29
Thanks for the tip, after installing the drivers from easyUbuntu and switching back from vesa to nv, I did notice a major performance increase. :)

---

### Post by confused57 on 2006-12-29
> **Cobski said:**
> Thanks for the tip, after installing the drivers from easyUbuntu and switching back from vesa to nv, I did notice a major performance increase. :)

I'm not speaking from experience, but if you've installed the nvidia drivers, you might want to try using the "nvidia" driver in your /etc/X11/xorg.conf file...which should enable 3D acceleration...easyUbuntu may have automatically changed it, I don't know...if there's no improvement, you can always go back to "nv".

---

### Post by Cobski on 2006-12-29
Thanks, that should help me out when I load up Doom 3.

---

