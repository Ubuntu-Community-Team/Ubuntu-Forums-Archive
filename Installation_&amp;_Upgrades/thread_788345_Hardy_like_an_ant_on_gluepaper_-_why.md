---
title: "Hardy like an ant on gluepaper - why??"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by endre on 2008-05-09
Hey guys - I've been a passionate fan of Feisty, used it, loved it, recommended it. It was fast, easy, and just worked. Hardy, not so much. Since installing it, I've almost given up getting any real work done in Ubuntu. 

The main problem is that everything... goes... so... slowly. Launching web browsers and other programs takes ages. Writing this, the text comes in short fits, rather than in a continuous flow. Watching videos, either it is video files, flash videos or DVDs is almost impossible due to lag. In Feisty I used to be able to have my documents up, Pidgin, Skype, maybe even a browser on another screen, and still watch DVDs without a hitch. That has become impossible. What on earth did Hardy do to my great system??

My computer is an Aopen 1557, with a 1,6 GHz intel centrino, 1Gb RAM, 128 Mb AVI Radeon Mobility (9700) and a 60 Gig hard drive. I've set all the graphics to a minimum, and it has unfortunately not solved the problem. Not that I would be willing to have them like that - grown addicted to the "flip-screens" of Compiz. 

ANY help greatly appreciated!

---

### Post by Pumalite on 2008-05-09
Go to System>Administration>Software Sources and enable ALL your repos; including backports and updates
Now:
sudo aptitude update
sudo aptitude upgrade

---

### Post by endre on 2008-05-09
Ok, tried it, and the user interface is slightly better, I can type without lag, for instance. The videos and dvds are still very laggy however. I can't watch anything without having several seconds of lag in image, while the sound for some reason works perfectly. So I can easily hear president Bartlett yelling at his staff, but the video looks like a lot of still photos. Graphics driver messed up?

---

### Post by Pumalite on 2008-05-09
ATI offers no support for Linux and you cannot campare it to an Nvidia card in Linux. The Nvidia Linux drivers are fine.

---

### Post by endre on 2008-05-09
Ok, so what do I do then? Should I use the community-supported driver instead? And why wasn't this an issue in Feisty, where actually Ubuntu worked much faster than Windows? Do I have to revert to Feisty to get it back to normal?

---

### Post by Pumalite on 2008-05-09
That's up to you, but my Hardy works fine with an Nvidia Card and is quite fast. The ATI proprietary drivers are known to mess up your system You could try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by endre on 2008-05-09
Yea, tried it already, found a thread in here on it - it helped, but only marginally. All desktop effects now work fine, but videos, and DVDs in particular are still in stop-motion. 

Currently using gstreamer though, could it be an option to try xine instead? See if it performs better?

---

### Post by Em-Buntu on 2008-05-09
I have an ATI x1600.
When I installed I decided to skip the ATI proprietary driver since the generic is working just fine.
You might what to uninstall the proprietary driver and see if it makes a dif.

---

### Post by endre on 2008-05-09
Ok, how to uninstall the proprietary driver safely? When I use the UI for hardware drivers, I am told that it is "in use" but clicking it only gives me the option of "enabling" it. In other words, it is in use, but not... how do I do it in the terminal?

---

