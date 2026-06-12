---
title: "Feisty Fresh Install: Volume controls not working"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by sque on 2007-04-23
I formated my desktop pc and installed Feisty (Beta) from the scratch. And every a little while, I upgraded my system with new updates till the final release of Feisty

The problem is that somewhere in the middle of updates (from the time beta was published till the final version), the keyboard volume controls stopped working.

**What happens**
When I press volume down or up, the pop-up windows shows and the volumes progress bar works but has no difference in sound. If the bar reaches the minimum, then it locks like muted (only visually) and I cannot raise it up again, but the sound is always the same.

**What is working**
Itsn't keyboard problem as the events are captured and handled very well.
The volume controll applet on the gnome panel works just perfect.
This was working out of box with 6.06 and 6.10 on the same pc.

I have no idea what to do, where to look for. I searched in the forum and haven't seen any similar problem. Plz help, any ideas. What's the responsible program that handles  volume control key events?

---

### Post by sque on 2007-04-24
bumb

---

### Post by YetAnotherNoob on 2007-04-25
I also have this exact problem.  Pop-up volume bar changes but the volume does not change.

---

### Post by YetAnotherNoob on 2007-04-25
OK.  I solved my problem ->I am a noob.  After reading the forums I fiddled with the applets and found a working combination.

I changed the applets to use my mixer not the Alsa mixer.  In system ->Preferences ->Sound I changed all Devices to use "STAC92xx Analog" the hardware mixer of my soundcard.

The changed Volume Control Prefrences in the volume applet to also use:"SigmaTel STAC9200 (OSSMixer) ".  Then selected The "Volume" entry in the tracks.

It now changes the volume using the volume keys.

:) 
Hope this helps any other newbies.

---

### Post by astroaniket on 2007-05-07
When I followed the instructions in the last post, I can hear test "beeps" but music and video players still don't give any sound. My device is also sigmatel 9221.

Any suggestions please?

---

### Post by astroaniket on 2007-06-09
(bump) anyone?

---

