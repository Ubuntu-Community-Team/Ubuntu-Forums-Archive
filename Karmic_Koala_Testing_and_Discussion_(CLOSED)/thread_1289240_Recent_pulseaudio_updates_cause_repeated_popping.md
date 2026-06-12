---
title: "Recent pulseaudio updates cause repeated popping"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-10-12
Just rebooted after installing the pulseaudio updates that came through within the last 12 hours. I now get loud and persistent popping (every 30 - 60 seconds, lasting for a fraction of a second). It's actually almost painful with headphones on. At the moment it doesn't seem to happen when audio is playing, so I think perhaps my Intel HDA soundcard is unsuccessfully trying to sleep.

Anyone else?

---

### Post by peddy on 2009-10-13
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/367544](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/367544)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433782](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433782)

Possibly related, I'm affected too.

---

### Post by Kazade on 2009-10-13
I'm also having this problem. With me it pops each time a sound starts to play. e.g., If I'm watching a video, it pops when the video starts, but then plays the whole video fine.

---

### Post by taavikko on 2009-10-13
Most likely cause by the powersave feature enabled on hda-intel chipsets.

---

### Post by MacUntu on 2009-10-13
To shut the thing up temporarily comment out the last line of /etc/modprobe.d/alsa-base.conf (something like "options snd-hda-intel power_save=10 ...").

---

### Post by whitethorn on 2009-10-13
+1 on the popping noise.  Commented out the power save function no more popping sound!!!!

---

### Post by cyberkilla on 2009-10-13
I've had this issue for weeks. Power saving on the audio card? Wow.

---

### Post by hanlin on 2009-10-13
I've had this issue for a while now too. I deleted the ~/.pulse folder and restarted, and it hasn't come back yet.

---

### Post by peddy on 2009-10-14
> **MacUntu said:**
> To shut the thing up temporarily comment out the last line of /etc/modprobe.d/alsa-base.conf (something like "options snd-hda-intel power_save=10 ...").

That fixed it for me. Removing ~/.pulse didn't.

---

### Post by EmmEff on 2009-10-14
> **MacUntu said:**
> To shut the thing up temporarily comment out the last line of /etc/modprobe.d/alsa-base.conf (something like "options snd-hda-intel power_save=10 ...").

Whew!  Thanks for this.  The popping was getting so annoying, I turned my speakers off.

---

### Post by surfed on 2009-10-19
> **MacUntu said:**
> To shut the thing up temporarily comment out the last line of /etc/modprobe.d/alsa-base.conf (something like "options snd-hda-intel power_save=10 ...").

Thank you. Now how can I make this permanent, so it will not be overwritten by an update or can we ask for this not to be included by default? My Soundcard goes directly into 150W Self-powered Studio Monitors and a 400W Sub, so you can imagine the volume of the pop when it comes back from powersave.

---

### Post by Rob2687 on 2009-10-19
That should make it permanent.

---

### Post by mjpatey on 2009-10-19
I understand that the devs are doing everything they can to make Ubuntu less power-hungry, and that's definitely a good thing!  But turning off sound after 10 seconds by default seems a little over-the-top.  Thanks for the quick and easy fix!!!

-Mark

---

### Post by surfed on 2009-10-19
Not everybody runs a laptop so it would be nice to have this as a setting somewhere rather than a text config. Like in Power-Managment, there should be an option between Laptop and Desktop mode.

---

