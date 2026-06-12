---
title: "Won't boot from USB"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by Zeroxje on 2012-07-07
Guys,

I've recently installed OpenSUSE on my laptop to test it out. Turns out I don't like it so I wanted to go back to Ubuntu. 

Now, I've created a a bootable usb stick with the Universal-USB-Installer.exe on my windows desktop and tested to see if it worked, which it did. 

Next I tried booting it from my laptop (F12 boot menu -> USB) I did the exact same thing while installing OpenSUSE which worked fine. However, as soon as I click USB almost immediately the bootloader grub/OpenSUSE thingey pops up. 

My laptop has 2 usb ports and tried 'm both. 

The thing is, I've tested the usb stick on my desktop and it worked fine. And 2-3 days ago I installed OpenSUSE using the exact same method on my laptop. 

Any guesses as to why this isn't working?

---

### Post by Zeroxje on 2012-07-26
So.. I've tried OpenSuse for a while longer and it still isn't working out.

Currently I'm stuck on "Syslinux 4.06 edd 4.06-pre1 copyright (c) 1994-2011 H. Peter Anvin et al"  with a blinking _ at the second line.

I know the USB stick is solid cause I've tried it on 2 machines and it booted into the ubuntu install/live cd screen.

any tips/help?

---

### Post by Rex Bouwense on 2012-07-26
I have one quick thing for you to check.  Insert the flash drive and turn the computer on.  Enter your BIOS and navigate to boot.  Some laptops recognize a flash drive as an additional hard drive so check the hard drive entry.  If there is a plus sign there or several entries, make sure that the fhash drive is a head of the hard drive in the boot order.  Just a thought.

---

### Post by Zeroxje on 2012-07-27
> **Rex Bouwense said:**
> I have one quick thing for you to check.  Insert the flash drive and turn the computer on.  Enter your BIOS and navigate to boot.  Some laptops recognize a flash drive as an additional hard drive so check the hard drive entry.  If there is a plus sign there or several entries, make sure that the fhash drive is a head of the hard drive in the boot order.  Just a thought.

I actually found out what it was, and I think a lot of people are having the same problem.

I only had the openSUSE distro on my laptop. For some reason a bootable USB stick created on a windowsmachine didn't work. But a Bootable USB stick created on the OpenSUSE distro worked immediately. I used the same .iso file for both of them.

I'm not sure this is working as intended, but when I've read through some of the threads on this sub-forum it seems like a lot of people are having this problem.

---

