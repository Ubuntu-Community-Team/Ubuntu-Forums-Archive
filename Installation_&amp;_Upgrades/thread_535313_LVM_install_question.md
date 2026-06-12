---
title: "LVM install question"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by ram100987 on 2007-08-26
I don't competely understand what LVM is.  I've been using feisty for several months now and have gotten the hang of all the basics and some the the intermediate tasks.  I recently have been trying to install feisty on the fiance's laptop to try and lure her away from windows.  I was having a lot of trouble with it.  The liveCD would never boot up, and using the text install it would only show a quarter of the screen.  Even when I fix the screen problem using the boot option vga=791 it kept getting stuck whenever installing the kernel or if it gets past that, when its load software.  Well I FINALLY got it to install using wubi, and then using LVM to give it its own partition. 

The issue is, I don't completely understand what LVM is or how it works.  I read an article about it and it was kind of confusing.  Can anyone put it in layman terms for me?

Also because of the way it was install it is still mounting the windows partition at startup and won't let me unmount it.  My guess is when the LVM put ubuntu in its own partition it carried over the settings that made the windows partition the host drive and forced mounting it.  Well now that I no longer need the windows partition to run, I would like to unmount it when not needed.

Sorry for the lengthy post but thanks for anyone that can give me some help!!!

---

