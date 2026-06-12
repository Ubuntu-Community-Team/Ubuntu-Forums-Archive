---
title: "Audio problem after upgrade to Hardy"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by hansengel on 2008-04-25
Hi,
I just finished upgrading to Hardy this morning, from Gutsy 7.10. It's been great so far, except for one thing--sound.

After upgrading to Hardy and restarting, I opened a music player and played some music. I heard little teeny sounds, but nothing significant. I checked the volume, and it was at its customary level. I cranked it all the way up, and doing so put it at just about the normal level of sound.

This is a bit odd--the speaker's volume is the same as always, and I didn't modify any sound options after the install. If you need diagnostics or anything of that sort, I'd be happy to provide them.

Thanks,
Hans Engel

---

### Post by Mystix on 2008-04-25
I have also installed xubuntu 8.04 upgrade and found that my sound is almost not there (so low you can barely hear it). I went into the sound settings and turned PCM al the way up and made sure everything was un-muted this helped some but still is about half volume of what it should be?

I have all the alsa components installed and it is recognizing my sound card.

KDS - Korean Data Systems
512 ram
40 GB Hard Drive
Xubuntu 8.04

---

### Post by hansengel on 2008-04-25
I got this fixed. I opened Volume Control (right-click the volume applet's icon in the panel) and brought the 'Front' device to its highest setting.

---

### Post by pdub on 2008-04-26
I had the same problem. I had to right-click on the volume control, select Open Volume Control, then File -> Change Device and change from Realtek to HDA Intel. Then as hansengel said, adjust the Front Volume.

---

### Post by techno-wiz on 2008-04-26
I had the same problem on my HP laptop. Raising PCM volume in the Volume Control Panel fixed it.

---

### Post by pedrorojo on 2008-04-26
well, I still have the problem, no joy on changing settings on ALSA mixer.
My audio is a realtek alc883
Any suggestions?

---

### Post by idiotonuni on 2008-04-26
I am not having trouble with the volume of speakers but with things not playing all together.  I will sometimes have trouble getting any music player to actually play the music for some reason.  Sometimes The music players work but I will pause them to listen to a youtube video in firefox, but the youtube video has no sound at all.  I have tried changing sound devices and everything so please help me.

---

### Post by Pumalite on 2008-04-26
> **pedrorojo said:**
> well, I still have the problem, no joy on changing settings on ALSA mixer.
My audio is a realtek alc883
Any suggestions?

Post:
lshw -C sound

---

