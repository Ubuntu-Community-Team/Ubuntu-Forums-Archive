---
title: "No mic recording in 8.04"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by sadris on 2008-05-10
I am trying to use ALSA to get my microphone to work under Wine (Ventrilo).

I can confirm that it works (Pulse can record from it, OSS can record from it).

I have installed a PCI sound card and my problem still exists in it (as well as my onboard mobo sound); I can hear myself breathing through the mic but gnome-sound-recorder cannot actually record data with any of the input devices selected. I am convinced that it is a configuration error. 

I do not have a .asoundrc file. I do not have any sound servers stealing the devices (Pulse, ESD, etc). ALSA is working, but I don't know how to tell it to record from the microphone.

Can someone please help?

---

### Post by Pumalite on 2008-05-10
Have you checked 'alsamixer' in your Terminal?

---

