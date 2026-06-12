---
title: "No weather and temperture icon"
date: 2008-11-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by phoogkamer on 2008-11-13
Hello,

I have installed Intrepid on my Acer 5051 and have configured timezone on the system the same way as with the Clock applet. After checking these were both the same, there was no weather and temperature icon now. Even though I have checked the boxes within configuration. 
The strange thing is that I have a desktop computer which had Hardy installed with the weather and temperature icon. After upgrading this desktop to Intrepid these icons with configuration were still there ande working. So upgrading works, but fresh install does not. Somebody has a solution?

---

### Post by frankleeee on 2008-11-13
I couldn't get the weather displayed via the clock but was able to with the weather applet in add to panel, right click on panel-add to panel-weather. I have a fresh install on this computer, o the 2 others it was a upgrade and it showed in the clock as you describe.

---

### Post by fballem on 2008-11-13
It is now a two-part process to setup the weather.

Part 1 is setting the clock up, which is now done through System > Administration > Time and Date. This is where you can setup NTP support. In Hardy, you used to be able to do this by right-clicking on the time display in the upper panel.

Part 2 is setting up the weather display. Right-click the display of the time (mine is in the upper panel on the right). If you select Preferences, then you can setup the location and weather information.

Hope this helps,

---

### Post by phoogkamer on 2008-11-13
That has worked for me too. Adding the weather applet from "Add to panel". I think that this one works better than the one with the clock, since this one gives me locations with weather stations to select from. Why is this not implemented in the weather icon form clock applet? I can remember that this worked with Hardy. Could this be a regression bug?

Tux

---

### Post by phoogkamer on 2008-11-13
Thanks Frankleee for the advice, but I am already aware of this procedure and the location of what to enable. I can imagen that this way of configuration is not userfriendly. Or am I mistaken? Is'nt it possible to add a list of locations with weatherstations to the configuration of the clock applet dependent on the time zone that is configured within the system?

Tux

---

### Post by phoogkamer on 2008-11-13
I have been adding my coordinates and location to the clock applet, but that does not give me the disired icons. Does anybody know how to debug this. When ticking the weather and temperature icon in Preferences I see a shift of the time text, but nothing is to be seen.

Tux

---

### Post by Gina on 2008-11-13
The weather for your home location was displayed with 8.04 but isn't in 8.10 - just one of many niggling little bugs still left.  But updates are still coming out thick and fast, so the devs are working on it all.

---

### Post by phoogkamer on 2008-11-13
Ok, fair enough. Can I help solving this? I am trying to figure out how I can debug this applet with dstrace and gdb. The clock applet is a module of gnome-panel. Can I use gdb by issuing the following command :
gdb /usr/lib/gnome-panel/libclock-applet.so [pid of gnome-panel]

:confused:

Tux

---

### Post by Dynaflow on 2008-11-20
I just figured out how to make the sucker work in Intrepid if it's being overly recalcitrant.  I have no idea why it works, but it did, on two separate (fresh) Intrepid installs.

Make sure you have time zones set congruently and such, and make sure you've set a location through the clock applet's preferences.  Then click the applet so the calendar comes down.  Now, click "Locations" to drop down the nifty sunshine map thing.

At the bottom of that area, you should see the weather information you so ardently wish to appear in the unexpanded version of the applet.  There's a button nearby it that says "Set" (it may be hidden until you mouse over it -- it's to the right of the city name)  Click it.  It will turn into a house once you put in your password, and voila!  Weather!

---

### Post by Gina on 2008-11-21
Well, I've tried everything including removing all locations except home and nothing makes the weather appear.

---

### Post by ronacc on 2008-11-21
Hmm I'm not having any problems with either the standalone weather applet or the clock applet weather report .

---

### Post by Dynaflow on 2008-11-22
> **ronacc said:**
> Hmm I'm not having any problems with either the standalone weather applet or the clock applet weather report .

When you set your location, do you remember doing it by right-clicking the clock applet and setting it through the Locations tab in Preferences, or did you set it via the buttons in the drop-down Locations box under the calendar?

---

### Post by ronacc on 2008-11-22
right clicking >preferences>location  also look at preferences>general and make sure display weather is checked .

---

### Post by phoogkamer on 2008-11-22
I have tryed all of the above, but nothing seems to work. The standalone weather applet works fine for me, but not the on with the clock applet. In the stand-alone version I can choose a location and do not have to fill in coordinates of my location. Isn't it possible to get location coordinates from google or something and then check for closest weatherstations for the weather section?

I can recall this being way easier with Feisty.

---

