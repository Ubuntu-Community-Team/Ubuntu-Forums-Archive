---
title: "Installing 6.10 on an external HD for use on a *different* machine"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by Zippy1970 on 2007-02-15
I have two Fujitsu Lifebook B110 (mini) laptops laying around collecting dust. These are Pentium 233Mhz MMX machines, one with 32Mb memory and one with 192Mb memory. Currently they have Win98SE installed and that runs perfectly fine. But I want at least one running a Linux distro, just for the heck of it. :) My desktop PC is dual  boot (XP and Suse 10.0), I have another machine running Debian, and since I've heard so many great stories about Ubuntu, I thought I'd give that a try. But to be honest, I'm not sure if *any* linux distribution with KDE or Gnome will even run with any decent speed on these laptops...

Anyway, this laptop doesn't have a CD-Rom drive and only a 3Gb internal HD. I removed the HD and put that in a external USB enclosure. I downloaded the 6.10 live CD and tried to install it on the 3GB HD (it recognizes it fine as /dev/sda). No problems there until just before it wanted to start the install. It told me it was going to install Grub on /dev/hda and obviously I don't want *that* (since I will be moving the 3GB HD back to the laptop). Plus I'm pretty sure that even if I get it to install Grub on /dev/sda instead, it won't work once I move the HD back to the laptop since on the laptop the drive will be /dev/hda...

So, is there a way to install Ubuntu on an external HD for use on another machine? Or are the machine specs so low that I shouldn't even bother?

---

### Post by Zippy1970 on 2007-02-16
Shameless bump?

---

