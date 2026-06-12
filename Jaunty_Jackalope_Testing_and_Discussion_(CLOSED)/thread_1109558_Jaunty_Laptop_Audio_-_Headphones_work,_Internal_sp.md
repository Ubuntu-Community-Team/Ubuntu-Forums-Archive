---
title: "Jaunty Laptop Audio - Headphones work, Internal speakers dont."
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by snowball1288 on 2009-03-28
Interesting issue...
Ive got an HP Mini 1033CL Netbook.

It seems that under jaunty i have a few of the common audio issues (starting up with audio muted).  but something else weird is going on.

After unmuting and turning up the volume in the gnome-volume-control, I get perfect sound from the headphone jack.  (perhaps worth noting that this netbook has a single headphone/mic combo jack).  However, without anything plugged in, i get no sound out of the internal speakers, nor do i see any headphone switch in the volume control.  any pointers?

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by sgosnell on 2009-03-28
There are several options in alsa, including front speakers, which may be turned off.  Start the alsa mixer, and see what is muted.

---

### Post by snowball1288 on 2009-03-29
figured it out!
it appears to be a problem that specific to this laptop.  

I followed the instructions here from mark:
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/64930](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/64930)

downloading the latest alsa drivers, compiling and changing the the alsa-base.conf file did the trick.  weird.  i can live with it, but for hte sake of those less motivated and with less free time on their hands, i hope that gets fixed soon.

---

### Post by Ubuntiac on 2009-03-30
Ugh. yes.

This one still has me tearing my hair out. :confused:

---

