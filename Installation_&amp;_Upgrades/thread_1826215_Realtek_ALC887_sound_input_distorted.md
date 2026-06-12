---
title: "Realtek ALC887 sound input distorted"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by philchambers on 2011-08-16
I am new to Ubuntu, though I have a lot of experience with RedHat server systems (so never bothered with sound on those).

I have just installed Ubuntu 10.04 LTS on a system which has an MSI H61M-E23 motherboard (Intel core i3 processor).  This has Realtek ALC887 sound on-board.  Initially I had no HDMI sound output available but this was fixed by going through Step 1 of

  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I still have a problem with sound input. Recording from the mic is very noisy and distorted and low volume.

I have checked the volume setting with the Gnome ALSA Mixer and all looks OK.

I have come across advice to find the model to use for the codec in

  /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

but ALC887 is not in there.

Can anyone point me to correct options to use in /etc/modprobe.d/alsa-base.conf please?

---

### Post by dino99 on 2011-08-16
other way to test:

gksu gedit /etc/modprobe.d/alsa-base.conf

and add at end of the file:

options snd-hda-intel model=auto
or
options snd-hda-intel model=generic

note: googling around "ubuntu+alc887" give some threads

---

### Post by philchambers on 2011-08-16
> **dino99 said:**
> other way to test:

gksu gedit /etc/modprobe.d/alsa-base.conf

and add at end of the file:

options snd-hda-intel model=auto
or
options snd-hda-intel model=generic

note: googling around "ubuntu+alc887" give some threads
Thanks for the suggestions,
I tried both (re-booting after each, of course).  'model=auto' had no effect on anything as far as I could see.

'model=generic' resulted in no input and no output.  It lost the HDMI output option, leaving just analogue options, and the mixer was reduced to just 'master', 'PCM' and 'Capture'.

The 'Level' display in the sound recorder showed lots of static with no sign of my voice registering.

I had previously tried lots of Google searches but could find nothing which helped.  A lot ended up pointing at the 'SoundTroubleshootingProcedure' web page.

---

### Post by steve11911 on 2011-08-18
I am wondering if one of the Studio distros might solve the problem.Some are Live cd's which makes them easy to try.

---

### Post by dr.micro on 2011-12-20
Same problem. OS Ubuntu 10.04 LTS + Realtek ALC887. After motherboard upgrade, I get no audio input from my mic. Audio out works perfectly.

---

