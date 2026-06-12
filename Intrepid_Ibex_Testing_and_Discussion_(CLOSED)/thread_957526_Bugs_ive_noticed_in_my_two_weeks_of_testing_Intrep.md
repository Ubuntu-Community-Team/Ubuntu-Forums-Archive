---
title: "Bugs ive noticed in my two weeks of testing Intrepid."
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by PlayEdUdE on 2008-10-24
Everything in intrepid seems to run smoothly for me with the exception of a few things All bugs listed were nonexistent in Hardy.

     System sounds got all switched around. (e.g. after update from hardy close window became clicking a button, startup and shutdown sounds are now non-existant) When i goto System>Preferences>Sound to change it, it doesn't work. Any changes made on the sounds menu have no effect. Only thing that works is toggling "play alerts and sounds on/off"
This bug has become especially annoying for me as i had the quake sound "HEADSHOT!" for close window now it does it everytime i click something and i cant change it.


     Video playback went wrong. Totem starts up fine but if i resize the window, raise/lower the volume, change playback position, or basically do anything at all, the window goes black filled in with garbage. Only workaround i've found is to fullscreen before playback starts and it seems to work smoothly then.

I haven't found any bug reports on launchpad for any of these and i was wondering if there is anyone else out there experiencing the same things that could confirm these.

---

### Post by shane19174 on 2008-10-24
System sounds have been discussed a lot here. The main complaint, however, has been that they stopped working altogether. Search the forum for libcanberra and you'll find the relevant discussion (and fix). I don't know about them getting mixed up, but maybe you just need to manually rearrange them or something?

The problem with animations has also been discussed, and for most people it's solved by resetting the problematic animations to their default values by clicking on the little yellow brush next to them (assuming you're using CompizConfig Settings Manager). Give it a try if you haven't yet.

Sorry I don't know anything about the video problem...

Shane

---

### Post by PlayEdUdE on 2008-10-24
is there anyway to reset the system sounds to defaults from the terminal?

---

### Post by shane19174 on 2008-10-24
Sorry, I don't know how to do that. Does that mean you can't open System > Preferences > Sound and try there?

---

