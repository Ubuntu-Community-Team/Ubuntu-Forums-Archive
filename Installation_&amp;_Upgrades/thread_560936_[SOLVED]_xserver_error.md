---
title: "[SOLVED] xserver error"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by stevepohler on 2007-09-27
I used the Alternate LiveCD and got all the way until I was in the command line, ready to "startx."
I do the command "startx" and I get:

fatal server error:

Caught signal 11.    Server aborting
XIO: fatal IO error 104 (Connection reset by peer) on X server  ":0.0" after 0 requests (0 known processed) with 0 events remaining.

My specs are:
Dell Inspiron 1420
Intel Core Duo 7300 @ 2.00 GHz
Mobile Intel(R) 965 Express Chipset Family
120 GB hard drive @ 5400 RPM

I have Vista already and I'm trying a 7.04 dual boot.

Any help would be great thanks.

---

### Post by TrickyXX on 2007-10-08
I have the same problem with my new Vostro... i think it's the Mobile Intel(R) 965 Express Chipset Family but i am not sure (linux newbie)... but i used Wubi to install ubuntu so i don't know if i can update the xserver with that :S 

i would really apprciate some help too...

---

### Post by dabl on 2007-10-08
Maybe this will help:

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)
:)

---

### Post by stevepohler on 2007-10-09
Thanks for the link, but I already did that.  From there I ended up where I am now.  I think that I'm going to wait for Gutsy on the 18th and hope that the driver is supported unless someone has a better idea.

---

### Post by dabl on 2007-10-09
I've been reading posts about newer hardware having problems with the *buntu splash screens.  There are a couple of relevant boot options that you could try on the boot line of /boot/grub/menu.lst.  One is "nosplash=y".  There are also several "vga=" options that resolve some splashy issues -- you might want to look at some of those.

:)

---

### Post by stevepohler on 2007-10-18
I waited for Gutsy and now things work perfectly, I think that my hardware was too new for Feisty.  Thanks for all the suggestions.

---

### Post by terry_saunders on 2007-10-19
Hi 

I had a similar problem. First of all I tried a Distro upgrade from Fiesty with no joy. After burning the Gutsy Alternate CD and reinstalling it works a treat. My hardware specs are near identical to the post.  Hope this helps others......

---

