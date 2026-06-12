---
title: "USB Skype phone not working after upgrade to 14.04"
date: 2014-06-24
forum: Installation &amp; Upgrades
---

### Post by Timothy Taylor on 2014-06-24
I have done a clean install of 14.04 and Skype.

I have tried for some hours to get Skype to recognise my USB VOIP Phone's microphone, without success.
Skype options\soundDevices lists "PulseAudio server (local)" (only) for mic, speakers and ringing.  Skype's output I play through my system speakers (that works fine) and I only use the mic on the USB VOIP phone.  Skype's call test does not recognise / replay any sound from the mic.

In the PulseAudio volume control, "VOIP Phone Analogue mono" section appears at the top of the Input Devices page, so the phone is recognised. The "sound level meter" shows the mic to be working.  Mic output does not seem to be getting to Skype for some reason. 

Any ideas?

---

### Post by Timothy Taylor on 2014-06-26
I installed the latest Skype s/w from their website and all works now.
:)

---

### Post by Timothy Taylor on 2014-06-29
Ha!
Spoke too soon - now it's back to being useless.

Any ideas???

---

### Post by Timothy Taylor on 2014-07-05
*bump*

I still have no mic working with Skype.

---

### Post by xc3RnbFO8P on 2014-07-05
Restart the computer and do **dmesg** in terminal and start Skype

---

