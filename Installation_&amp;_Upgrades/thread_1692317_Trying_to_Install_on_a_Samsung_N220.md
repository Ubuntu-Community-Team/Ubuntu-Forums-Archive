---
title: "Trying to Install on a Samsung N220"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by Castaras on 2011-02-21
Hi, I'm trying to install for a dual-boot with Windows Starter the Ubuntu remix on mine and my dad's netbooks ([This one specifically]("http://www.amazon.co.uk/Samsung-Netbook-1-66GHz-Windows-Starter/dp/B004KSRVPU/ref=sr_1_1?s=computers&ie=UTF8&qid=1298295262&sr=1-1")). However, we're running into some problems when trying to get the installation to work.

We've been booting it from a USB chip using [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"), and when just booting it from the memory chip it's been working fine. 

However, when we try to install it, we have the following problems:

[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/install_03_medium.jpg[/IMG] 
According to this picture, we should have three options. On our computer we're not getting the first option (Which is the one we want...).

On trying to use the Manual specification of partitions, we have 4 partitions shown - an sd1, an sd2 (presuming these are for windows), sd3 (C: drive), and sd4 (D: drive). We decreased the size of D drive(from 140 to 70) so as to give us some free space to put the Ubuntu installation in. Instead of getting sd4 (70gig) and some free space (70gig) to give us space to add in the place for the ubuntu installation, we got 70 gig of "unusable" (which is still there on my dad's computer which we can't get rid of!).

I'm clueless on what to do now. Any ideas? We'd read somewhere that the N220 doesn't work with Ubuntu due to its Intel Atom N450. Should we be looking at a different Linux distribution?

---

### Post by Dutch70 on 2011-02-21
To give a better idea of your partitions to anyone that may be able to help, open Gparted and take a screenshot. Save it to your desktop & attach it to your next post. 

eg. This is mine

---

### Post by Castaras on 2011-02-21
> **Dutch70 said:**
> To give a better idea of your partitions to anyone that may be able to help, open Gparted and take a screenshot. Save it to your desktop & attach it to your next post. 

eg. This is mine

Hah, I'd just come back to update with the fact that we've got back the unusable data storage into our D drive. It's mainly the first problem we need help with - we just want the two operating systems dualbooting on the computer.

---

### Post by Castaras on 2011-02-27
Bump. We've managed to sort out one netbook with a pure install of Ubuntu (I don't need Windows 7 on my netbook, dad does). However, dad's netbook still gives us only two options for installation of Ubuntu. Strangely enough, before the first install of Ubuntu on my own netbook, we only had the bottom two options shown in the screenie in the first post, but after an unsuccessful install, we got all 3 options... would be perfect except for the fact it was install ubuntu alongside ubuntu.

The netbook we want dualbooting has already had windows 7 starter sorted out and with some files on it (backed up already, we don't want to lose them while messing with OSes!). We've tried Ubuntu from the memory chip multiple times and loved it. Umm... Not sure what information is needed, any ideas? :confused:

---

### Post by Dutch70 on 2011-02-28
Not sure if it will help, but can you post a pic of your partitions in Gparted?

---

