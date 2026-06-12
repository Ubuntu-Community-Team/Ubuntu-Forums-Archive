---
title: "skype in jaunty 64bit won't start"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pottedmeat123 on 2009-04-13
I had previously had Skype working with sound going to a USB telbox and a regular handset... I was using 8.10 64 bit and the whole setup was working fine.

I just upgraded to Jaunty and now I can't get skype to start. I installed skype-static from Medibuntu, but when I try to boot it in a terminal this is the error I get:

/usr/bin/skype.real: relocation error: /usr/bin/skype.real: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference

I'm still a bit new with Linux, so I'm not sure where I can go from here. I have pulse-audio installed..., is there something I can do there? Is this just another issue being sorted out before the release, or is there something I can go to get this working now?

Oh, as a side note, I did replace my skype with skype-static-oss, also from the Medibuntu repo. That actually DID work, but the audio was really wonky. Whenever the phone was picked up, there would be a loud hiss out of the computer speakers, or sound would break-up pretty badly.

---

### Post by nandemonai on 2009-04-13
Works fine here. Try removing and reinstalling completely.

---

### Post by pottedmeat123 on 2009-04-13
I tried doing that multiple times. I reinstalled the .deb I had originally installed prior to upgrading. Then I pulled the one off Medibuntu and installed that (as well as static and oss versions.) I uninstalled and reinstalled it several more times but still with the same error. 

Short of unclicking the packages in Synaptic and refreshing, is there any way to uninstall more completely? Some package I'm missing?

---

### Post by nystire on 2009-04-13
When you uninstalled the package, did you use the 'remove' option or the 'completely remove' option? The first only removes the binaries, while the second also removes the configuration files.

---

### Post by pottedmeat123 on 2009-04-15
Ok, tried that. Reinstalled the Medibuntu package and rebooted. Exact same error.

---

