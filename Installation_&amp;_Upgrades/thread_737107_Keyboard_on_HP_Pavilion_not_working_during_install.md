---
title: "Keyboard on HP Pavilion not working during installation"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by equal on 2008-03-27
[I]**ISSUE HAS BEEN SOLVED*** I simply entered the BIOS and disabled the Legacy Universal Serial Bus. Everything works now!!
****************************************[/I]

I've looked through a few forum threads, nothing quite covered this issue. I just picked up an HP Pavilion a6207c. I was really happy with my choice. Almost everything in it is Linux friendly, nVidia graphics etc etc.

But I have a weird problem. I insert the Ubuntu installation disc, and once the installation screen comes up, the keyboard is non-functional. It works during the disc bootup (selecting the installation option, etc), and it does it with both an 8.04b disc and a 7.10 disc.

I've tried this using two different ps2 keyboards. And like I mentioned, both worked during the boot phase, it's only once the OS is installing that it fails. They work fine on my Win XP installation.

I've downloaded the 8.04b alternate disc, we'll see if that helps.  But if you have any other ideas, I'd love to hear them!

---

### Post by nebu on 2008-03-27
maybe ur keyboard is not properly set up.... 

maybe u have some keyboard which isnt the standard us english type and u are configuring ur keyboard wrong!!

just try this after u know exactly what keyboard u have....
> sudo dpkg-reconfigure xserver-xorg

---

### Post by equal on 2008-03-27
Yes, it will be slightly hard to type that command in without the use of my keyboard, mind you. ;)

---

### Post by equimen on 2008-04-27
Hello
I have the same problema with my HP Pavilion dv5000, if you could please explain in detail how you fixed it, because I cant find what you mentioned ("I simply entered the BIOS and disabled the Legacy Universal Serial Bus.")

Thanks in advance

---

### Post by matthewhunt on 2008-04-29
Ahaa, I have the same problem when running 7.10 live cd on my desktop. I'll try that solution tonight.

---

