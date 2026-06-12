---
title: "Blank Screen on boot, but system is working. On AMD A6-3650 - Ubuntu 11.10 64bit"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by ieracos on 2011-10-14
Hi, I've just upgraded to Oneiric Ocelot 11.10 (from 11.04), but on the reboot I got a blank screen. My system is based on a Llano CPU+GPU by AMD, the A6-3650 and is the 64 bit version.
It's all ok till the grub menu, but after I select the kernel image to boot, a purple stripe appears on the upper part of the screen for just a moment, and then I got a blank screen and the monitor enters in standby.
The strange think is that I know that the system continue to load correctly, even the desktop environment: infact if I type in my password (after I hear no more loading in course) I can hear the system loading again. I can also switch to a virtual terminal and enter some commands: I use this to shutdown the system.
I tried to change some things on the grub menu but nothing has changed. The only way to make it boot correctly is to add the "nomodeset" to the kernel parameter, but this way the X server doesn't load up.

---

### Post by collisionystm on 2011-10-14
> **ieracos said:**
> Hi, I've just upgraded to Oneiric Ocelot 11.10 (from 11.04), but on the reboot I got a blank screen. My system is based on a Llano CPU+GPU by AMD, the A6-3650 and is the 64 bit version.
It's all ok till the grub menu, but after I select the kernel image to boot, a purple stripe appears on the upper part of the screen for just a moment, and then I got a blank screen and the monitor enters in standby.
The strange think is that I know that the system continue to load correctly, even the desktop environment: infact if I type in my password (after I hear no more loading in course) I can hear the system loading again. I can also switch to a virtual terminal and enter some commands: I use this to shutdown the system.
I tried to change some things on the grub menu but nothing has changed. The only way to make it boot correctly is to add the "nomodeset" to the kernel parameter, but this way the X server doesn't load up.

Reboot

Immediately after bios hold the shift key

you will be at the grub menu

choose system rescue

hit resume normal boot and hold the shift key down until you get to the boot prompt

put in your login credentials

sudo apt-get install fglrx

reboot

you should be good.

---

### Post by ieracos on 2011-10-14
Thank you very much! It worked perfectly =)

---

### Post by Sonja on 2011-10-15
I am trying to solve the same problem with the black screen and the mouse cursor as a large X. Also, while starting up, it says "waiting for network configuration".

These problems happened to me after the upgrade to Oneiric. I tried a fresh install, and the same problem is still occurring.

My machine is Asus UL30VT.

Is 'system rescue' the same thing as 'recovery mode'?

---

### Post by nitrogen15 on 2011-10-15
> **Sonja said:**
> Is 'system rescue' the same thing as 'recovery mode'?

It's the same.

---

