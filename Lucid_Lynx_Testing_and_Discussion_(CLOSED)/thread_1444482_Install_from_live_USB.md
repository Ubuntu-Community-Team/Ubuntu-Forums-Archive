---
title: "Install from live USB"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by chriscrifasi on 2010-04-01
Greetings, this is my first post so my apologies if it is in the wrong area. 

I was having a problem getting my Lucid beta to boot after a bad update so I attempted to go in through a "live" session off of a USB stick.

I attempted to "chroot" and dorked things up. I tried to install Lucid from the "live" USB but it said that my disk is full. It is attempting to install Lucid on the USB.

How do I tell it to install on my hard drive and not on the USB?

Thanks

Chris

---

### Post by VMC on 2010-04-01
> **chriscrifasi said:**
> Greetings, this is my first post so my apologies if it is in the wrong area. 

I was having a problem getting my Lucid beta to boot after a bad update so I attempted to go in through a "live" session off of a USB stick.

I attempted to "chroot" and dorked things up. I tried to install Lucid from the "live" USB but it said that my disk is full. It is attempting to install Lucid on the USB.

How do I tell it to install on my hard drive and not on the USB?

Thanks

Chris
Without knowing your HD layout its hard to diagnose the problem. You use used "Startup Disk Creator" to the usb flash drive?

then you booted with that flash drive. Is this correct?

Sounds like something up with your partitioning. 

Output '*sudo fdisk -*l' and '*sudo blkid*' so we can help you.

---

### Post by chriscrifasi on 2010-04-01
> **VMC said:**
> Without knowing your HD layout its hard to diagnose the problem. You use used "Startup Disk Creator" to the usb flash drive?

then you booted with that flash drive. Is this correct?

Sounds like something up with your partitioning. 

Output '*sudo fdisk -*l' and '*sudo blkid*' so we can help you.

Sorry not sitting in front of my computer, its at home.

Yes I had used Startup Disk Creator to create the USB flash drive when everything was working correct. 

I can only run those commands while using the live USB, will that give you what you are looking for? As you can tell I am quite new to Linux.

I do know that my main partition is /dev/sda1/

---

### Post by VMC on 2010-04-01
How did you end up on this forum?

Usually new users start asking questions in the main forum. We have several sub-forums for any related questions.

Lucid won't be released for a while, we are still on beta1. If you do decide to install it, don't expect it to run smoothly for now.

To answer your question, use the "Try Ubuntu without installing" menu. When it boots up, go Applications > Accesories > Terminal, then type in 'sudo fdisk -l' without quotes, Copy & paste the results back here.

---

### Post by chriscrifasi on 2010-04-01
> **VMC said:**
> How did you end up on this forum?

Usually new users start asking questions in the main forum. We have several sub-forums for any related questions.

Lucid won't be released for a while, we are still on beta1. If you do decide to install it, don't expect it to run smoothly for now.

To answer your question, use the "Try Ubuntu without installing" menu. When it boots up, go Applications > Accesories > Terminal, then type in 'sudo fdisk -l' without quotes, Copy & paste the results back here.

Yes , I realize that its a beta and won't run smoothly. I have reinstalled the OS 3 times so far, which usually isn't a problem as all of my data is "in the cloud". However, this time I'm having problems re-installing from the USB>

Thanks for the info about Terminal and fdisk.

---

### Post by jmmL on 2010-04-01
I had problems with "disk full" type errors when installing on LiveUSB. It seems when the area used for persistent storage on the USB stick fills up, you can't install properly.

My solution was to clear the cache etc in firefox, which freed up enough room for the install to go smoothly. It sounds like this will work for you as well.

---

