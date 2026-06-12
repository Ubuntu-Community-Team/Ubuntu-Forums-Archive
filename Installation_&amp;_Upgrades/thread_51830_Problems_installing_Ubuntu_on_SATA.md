---
title: "Problems installing Ubuntu on SATA"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by robbish on 2005-07-25
Hey.

I am trying to install Ubuntu on a computer with SATA-hds. The problem is; the installation cant find the disks. It just says, "Cant find any harddrives" or something like that. I have tried booting Gentoo livecd, to check if it would find them. They where called sda,sdb just as i thought.. But how do I get Ubuntu to understand that? :P 

Thank you, in advance. :)

//robbish

---

### Post by flip on 2005-07-25
I had a similar problem with my SATA on first Ubuntu install (I've never messed with Gentoo so mine might have worked there too). You'll probably have to track down info about your particular SATA controller. 

Personally my Dell 8400 shipped with a version of XP equipped with special drivers and Ubuntu didn't know how to talk to my SATA either. I had to go into my BIOS and play with the controller settings. I had success putting the SATA into what they term'd "combination mode" (whatever that means). On my next boot my drives showed up fine as sda etc. The drives may be running a bit slower this way, but I can't tell (how to bench mark this would be interesting  ;-) ).

Best advice I can give you is search through linux hardware specific forums looking for your SATA controller. If Gentoo can see them correctly Ubuntu should be able to also (jumping through hoops may be required).

Cheers and good luck

- flip

---

