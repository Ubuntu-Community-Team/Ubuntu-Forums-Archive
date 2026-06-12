---
title: "Edgy Eft Sound"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by benndamann33 on 2006-11-16
I just recently updated to edgy eft and for some reason I lost my sound of my computer - any suggestions(using dell latitude D610 laptop)

---

### Post by Gaweph on 2006-11-16
This happened to me. But for me was a simple case of changing the default soundcard back to my pci one.

Maybe try looking at the alsa mixer, sometimes the volume gets put onto mute, or very low at upgrades or new installs.

Open Alsa mixer and turn everything up would be my suggestion...

---

### Post by benndamann33 on 2006-11-16
yeah turned everything up to 100%, still no luck. any other suggestions? thank you

---

### Post by benndamann33 on 2006-11-16
nothing else guys?

---

### Post by ryan on 2006-11-16
> **benndamann33 said:**
> nothing else guys?

I am having a similar problem and am going through the forums now reading up on the issue search for "sound" or "sound config files" or sound problems. Check out the multimedia thread.

---

### Post by Gaweph on 2006-11-17
Soundcard drivers.  I once had to compile a driver for my Soundblaster 24bit card.  You may have to search for a new driver that will work with edgy.  Although if it worked with dapper this probably isnt the problem..  Just a thaught.

---

### Post by iAlta on 2006-11-17
I had the same problem.( from HH to DD)

All I had to do was to turn off the system sound in th BIOS.

But if you had it in Drapper, I don't know if it works..

---

### Post by benndamann33 on 2006-11-18
turn it off in the bios?

---

### Post by mgmiller on 2006-11-18
I have had some weird hardware issues that were resolved by turning the device off and on in the BIOS.  Before trying that, try a complete power off and unplug the power cord to the computer.  Give it a min. or so and plug it back in and boot it up.  If you still have the sound problem, even though all the software says it should work, then reboot, go into your BIOS (the key strokes needed to do this vary by manufacturer, some popular ones are the delete key and f10 key.  See if there is a message during POST that says press "some key" to enter setup.  Once there, look around for your onboard sound card option and disable it.  F10 usually saves the new configuration, exit BIOS and reboot.  Then reboot again, go back into BIOS and turn the sound card back on.  F10 (or whatever your mobo requires) to save it and exit and reboot.  With a little luck, the sound card will now work.

---

### Post by linxtst on 2006-11-18
I solved my "no sound" problem by disabling the sound in BIOS.

Now it works perfectly. :-D

---

### Post by benndamann33 on 2006-11-18
superb - works again - that's a weird error. Thanks guys

---

