---
title: "Sound problems after upgrade to edgy"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by ianhaycox on 2007-02-01
After upgrading to Edgy from Dapper I have lost my login/logout sounds.

I get a sound (da dum) when Gnome prompts for the username/password (/usr/share/sounds/question.wav) but then no startup sound.

Checking in Sound Preferences show 'Play System Sounds' is enabled, but clicking on the play button for Login and Logout is slient.

Sound works OK in Rythmbox, Firefox and Totem movie player, I can even play /usr/share/sounds/login.wav and logout.wav via Totem.

Worked fine before the upgrade. The upgrade worked really well, a couple of minor problems with usplash and swap signatures, but they have been fixed thanks to this forum.

Any ideas anyone ?

---

### Post by ianhaycox on 2007-02-02
After running gnome-sound-properties in a terminal I noticed a number of errors related to ESD which lead me on to reveal [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME)

Everything now works.

---

