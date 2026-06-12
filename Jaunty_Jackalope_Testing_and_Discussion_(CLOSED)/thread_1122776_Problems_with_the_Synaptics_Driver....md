---
title: "Problems with the Synaptics Driver..."
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rowanq on 2009-04-11
Since I moved to Jaunty Beta, I've been having a problem with my touchpad.

I had edited my .fdi to use corner taps; middle and right buttons in the upper left and right corners, back and forward buttons in the lower left and right.

But for some reason, the touchpad would randomly register a button 8 event (back button) causing the browser to navigate away from a page instead of click a page element. In each case, the button 8 event would happen when tapping on the right side of the touchpad, opposite the corner that button 8 was assigned to. I have confirmed this with xev.

I have since commented the navigation buttons out of the .fdi to avoid this.

Has anyone else had this issue? Is it a know issue with driver? I have used mostly the same configuration flawlessly with previous versions of Ubuntu, though I used xorg.conf.

Any help is much appreciated.

Rowan

---

### Post by rowanq on 2009-04-13
Nobody? 

Additional info; no matter what I assign to that corner, it shows up and gets triggered on the other side of the touchpad. So if I make LBCornerButton == 3 I get a spot in middle of the right side of the pad that triggers button 3 events.

Any help or suggestions would be great.

---

### Post by rowanq on 2009-04-15
Filed a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/361906](https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/361906)

I downgraded to synaptics 0.15.2 as a workaround. Get it here:

[http://launchpadlibrarian.net/20438229/xserver-xorg-input-synaptics_0.15.2-0ubuntu8_i386.deb](http://launchpadlibrarian.net/20438229/xserver-xorg-input-synaptics_0.15.2-0ubuntu8_i386.deb)

---

### Post by ildfroe on 2009-04-15
I dont use the touchpad much, I use a mouse.
So I haven't noticed those issues, but tapping stopped working.
Downgrading solved this.

---

### Post by Sarvatt on 2009-04-18
> **rowanq said:**
> Since I moved to Jaunty Beta, I've been having a problem with my touchpad.

I had edited my .fdi to use corner taps; middle and right buttons in the upper left and right corners, back and forward buttons in the lower left and right.

But for some reason, the touchpad would randomly register a button 8 event (back button) causing the browser to navigate away from a page instead of click a page element. In each case, the button 8 event would happen when tapping on the right side of the touchpad, opposite the corner that button 8 was assigned to. I have confirmed this with xev.

I have since commented the navigation buttons out of the .fdi to avoid this.

Has anyone else had this issue? Is it a know issue with driver? I have used mostly the same configuration flawlessly with previous versions of Ubuntu, though I used xorg.conf.

Any help is much appreciated.

Rowan

I have an updated driver if you want to try it in my PPA

[https://launchpad.net/~sarvatt/+archive/ppa](https://launchpad.net/~sarvatt/+archive/ppa)

Some things of note - gsynaptics is made for the ancient .15 drivers, uninstall it if you're using anything newer because it's broken pretty bad. SHMConfig is no longer required in versions >1.0.0, you can do everything through x properties or synclient without SHMConfig now. gpointing-device-properties is the new gsynaptics if you need a gui to manage it. If you have problems building that just post and I can help. You can do a man synaptics to see the new options after installing it.

---

### Post by rowanq on 2009-04-20
Sarvatt,
 Sorry for the late response. I installed the synaptics .deb from your PPA, but the bug persists. Gonna stick with .15.2 for now (which is a shame, 'cause I really wanna move to the 1.xx drivers.)

---

