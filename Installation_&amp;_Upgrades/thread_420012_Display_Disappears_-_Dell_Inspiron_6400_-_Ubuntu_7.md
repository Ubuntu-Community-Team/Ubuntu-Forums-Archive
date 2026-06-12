---
title: "Display Disappears - Dell Inspiron 6400 - Ubuntu 7.04"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by someone589 on 2007-04-23
Hello,

I just downloaded and attempted to install ubuntu on my laptop. But after a minute or so the display disappears.

I see the initial install screen.

I click on the installation option.

I see the Ubuntu logo together with the progress bar which moves side to side.

and then suddenly everything disappears.


I am using a Dell Inspiron 6400, and Ubuntu 7.04

any ideas?

Thanks

p.s. Am not a linux expert.

---

### Post by someone589 on 2007-04-23
The video card is an ATI Mobility Radeon X1400

---

### Post by pertti on 2007-04-25
I think you've come across a bug related to ATI X1xxx cards which is giving headaches to a lot of people. Thankfully there are workarounds. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?p=2516434"), which is specifically for a Dell 6400 with an ATI X1400. That guide tells you how to install Ubuntu 7.04, set up the ATI card, set up Beryl (those 3D desktop effects), and the Dell 1390 wireless card (if you have an Intel it should work right out of the box, i guess).

That guide assumes you downloaded the alternate CD and not the live one. The alternate has a text installer, while the live one lets you try Ubuntu before you decide to install it and has a graphical installer. In case you only have the live CD try what [this post]("http://ubuntuforums.org/showthread.php?p=2516434#post2516434") says (Note: to go to the command line when X crashes hit Ctrl+Alt+F6).

---

