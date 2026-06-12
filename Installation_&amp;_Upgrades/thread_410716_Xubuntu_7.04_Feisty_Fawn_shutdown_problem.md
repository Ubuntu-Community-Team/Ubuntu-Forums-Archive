---
title: "Xubuntu 7.04 Feisty Fawn shutdown problem"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by raycherng on 2007-04-16
I've installed Xubuntu 7.04 Feisty Fawn
I installed on my Acer laptop
It's really beautiful and faster than the previous Ubuntu 6.10 
But I found  when I shutdown the Xubuntu
It won't power off itself
I must turn off the power manually
Can anyone help me to solve this problem

(I've install by alternative edition with acpi=off and noapci option to make installation success 
on my previous Ubuntu 6.10 I also install  alternative edition with acpi=off and noapci option to make installation success.It work fine without the shutdown problem)

---

### Post by raycherng on 2007-04-18
I solved the problem!!
I add
**apm power_off=1**
to  /ETC/MODULES

and my laptop power off ~~

---

### Post by banksam on 2007-04-21
I have the same problem on my thinkpad r51e.  This solution doesn't work for me.

Are there any other suggestions please?

---

### Post by earonoff on 2007-05-02
This worked for me also (Kubuntu 7.04):

I solved the problem!!
 I add
 apm power_off=1
 to /ETC/MODULES
 
 and my laptop power off ~~

Tnx to RAYCHERNG

Ethan

[email]earonoff@ca.rr.com[/email]

---

### Post by intangir1999 on 2007-05-31
I have the exact same problem and I've tried both solutions without avail:

The first attempt was adding the acpi=force to the /boot/grub/menu.lst 
this did not work.

The second was this past solution of adding apm power_off=1 to the /etc/modules file
this also did not work.

I am running Xubuntu on a Toshiba Satillite Pro 4300 Series (nicely going), but for some reason I only get the Xcfe shutdown screen (haven't been able to get the boot script to appear on startup or shutdown), and when the status bar finishes being "emptied" it just hangs there.  This happens whenever I use the shutdown button or even do an "init 0" as root.

Any one else have a possible solution for this?

---

### Post by intangir1999 on 2007-06-01
Scratch that last post, after installing Startup Manager and enabling text upon startup, I was able to shutdown successfully.  I don't know if it has to do with the Splash Screen, but this may be something to be looked into.

---

### Post by proshanto on 2008-04-15
Thanks for the apm power_off=1 tip, ray...
What if I am just trying to feel Xubuntu from Live CD? I have not wiped off my Win XP yet, that's why. Any help, any body?

---

### Post by zombrax on 2008-04-16
i have this problem when i get the laptop to restart!! anyone can help me out with this one? 

many thanks :)

---

