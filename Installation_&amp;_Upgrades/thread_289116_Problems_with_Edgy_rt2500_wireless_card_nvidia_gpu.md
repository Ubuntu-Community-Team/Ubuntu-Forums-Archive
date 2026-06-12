---
title: "Problems with Edgy: rt2500 wireless card nvidia gpu"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by edieguez on 2006-10-30
Hi,

I recently upgraded to Edgy and I have two annoying problems. The first is with my wireless card. Its rt2500-based and it took me ages to get it working on my machine (using WPA). Unfortunately, since upgrading to edgy I've noticed network access does not come up unless I manually start up the network by going through the wireless configuration KDE module. I have to click 'Disable interface' and then 'Enable interface'. This was not true before my upgrade. I've tried using Knetworkmanager but my wireless card does not appear in the options - it doesn't seem to know I have a wireless card, which is strange.

Second, I have a strange color problem. Whenever I log onto X-windows, my colors are subtle shifted in the sense anything black shows up with a rainbow of dark colors. For example, anything black might show up with splotches of dark green and red. If I open up the NVIDIA driver (using the graphical module), the screen blinks and then color shift vanishes - the problem is fixed. This did not happy before the upgrade either!

Any help in either matter would be greatly appreciated.

---

### Post by GadgetsGuy on 2006-10-30
here is the configuration you need for your rt2500-based wireless device:

[http://www.hotubuntunews.com/blog_2.shtml](http://www.hotubuntunews.com/blog_2.shtml)

please give me a digg if too ;)

---

### Post by edieguez on 2006-10-31
I already did that when I first set up Dapper and it did work. But since upgrading the Edgy the network won't auto start. I am forced to go through the Network Module, click on ra0, click on 'disable interface' and then 'enable interface'.

---

### Post by heinkel_111 on 2006-11-07
Regarding the color problem, me and 2 other users have reported similar problems (although we are kubuntu users, this goes beyond K/Ubuntu duvude I think. 

[Original thread on Kubuntuforums](http://kubuntuforums.net/forums/index.php?topic=10686.0)

[Thread here on Ubuntuforums](http://www.ubuntuforums.org/showthread.php?p=1728296#post1728296) (same problem description, but easier to answer if you haven't any other reason to register at Kubuntuforums).

---

### Post by Spitphire on 2006-11-09
try adding the option diableirq in your xorg.conf under your video card drivers..

---

### Post by heinkel_111 on 2006-11-10
diableirq???

disableirq, you mean?

What does that option do? (I like to understand what is required to make it work :) )

---

### Post by Spitphire on 2006-11-15
Sorry for the late reply, sorta forgot about the forum.. anyway...

edit xorg.conf 
and add:

Option          "DisableIRQ"

reset everything, and your wireless card should work - I'm guessing you have VIA drivers along with the rt2500...

Hope this helps, if not - i'll check for a reply and try to get back to you...

---

### Post by voam on 2007-03-07
I am also having problems with Edgy, the rt2500 driver, and an nvidia card. I can connect ( and stay connected for quite some time), but then it disconnects from the access point and often won't reconnect no matter what I do. I hope this fixes the problem.

---

