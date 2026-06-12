---
title: "Microphone patch for Ubuntu 9.10 on EeePC 900a"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sven6210 on 2009-10-12
I have installed **Ubuntu 9.10 Beta** on my **EeePC 900a** yesterday and I am very excited about it. Even though it is still the Beta it works very well and I did not face any trouble so far.

What I like about the new Ubuntu 9.10:
- It feels quicker than Ubuntu 9.04 UNR respectively eeebuntu 3.0
- I like the new NBR desktop, looks very modern and functional
- I only needed to make one small adjustment to get the microphone and Skype to work
- Except the Wifi all other 'FN' keys work out of the box

In order to get the microphone to work when using Ubuntu 9.10 Beta on an EeePC 900a you only need to patch the ALSA configuration file:

**Patching of the ALSA configuration file (/etc/modprobe.d/alsa-base.conf)**

1. Open a terminal window
2. Enter 'sudo gedit /etc/modprobe.d/alsa-base.conf'
3. Search in the file whether a line including 'snd-hda-intel' exists, if so please delete that line
4. Add the following two lines to the configuration file:

===start here===
# eeePC 900a patch
options snd-hda-intel index=0 model=quanta
===end here===

5. Save the ALSA configuration file and close the editor (gedit)

Have fun with Ubuntu 9.10, it is a great look & feel OS for the EeePC 900a

---

