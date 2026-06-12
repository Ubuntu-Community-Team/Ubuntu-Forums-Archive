---
title: "Pulseaudio: multiple sound cards with volume controls"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ceverett on 2009-04-19
I've got Jaunty up and running on a Dell Latitude E4200.  The only thing I did differently was to set up tmpfs partitions for /tmp, /var/tmp, var/log/ and my firefox profile, and run without a swap file, so as to minimize writing to the SSD.

So far, the out of the box configuration of pulse seems to work 90% OK. 

The first issue is that under System > Preferences, there are 2 sound control panels with identical icons, both labeled "Sound".  The first one is definitely associated with pulse, and the second one looks to be the same one as the one from Intrepid.

The main issue I am having is that my USB sound card has a volume control, as does the laptop.   By default, all of the volume control knobs control the vlume of the default mixer track set on the old sound control panel.

What I would really like it to make it so I can control the volume of my usb-audio card with the volume knob on it, and the volume of my built in sound card with the buttons on the laptop.

Does anyone have any clues for me on this?

---

### Post by crimsun on 2009-04-19
> **ceverett said:**
> What I would really like it to make it so I can control the volume of my usb-audio card with the volume knob on it, and the volume of my built in sound card with the buttons on the laptop.

Does anyone have any clues for me on this?

Use xev and script the events to use amixer.

---

