---
title: "No Sound after upgrade to 10.04"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by CaronMargarete on 2010-05-11
Completed the upgrade to Lynx from Koala and now have no sound. There's also no icon in the bottom panel. 

What information do you need for me?

I'm a very new user to Ubuntu and not accustomed to tech-talk, please help with super clear instructions so I know exactly what I need to do. I've looked throughout this forum for other advice but none seemed the same.

Many thanks.

---

### Post by mörgæs on 2010-05-11
If you boot with a 10.04 live CD, do you have sound? 

Have you checked sound controls and mixers and verified that they are all high? Muting not accidently checked? (Not to insult you, these are common mistakes).

---

### Post by CaronMargarete on 2010-05-11
I've got no ability to load with CD. 

Also from what I can tell all the sound is on, not muted, and are set to high but perhaps you'd like to clarify exactly which programs I should use to check because there seems to be a few...

Thx.

---

### Post by mörgæs on 2010-05-11
Which machine do you have? It must be possible to boot eigther from a CD or a USB drive.

I was thinking of Alsamixer or Alsamixergui.

---

### Post by CaronMargarete on 2010-05-11
Sorry I wasn't clear. Yes it technically is possible to boot from USB or CD because I have an ACER Aspire 4535, however I didn't boot from a CD originally, in fact never have with any upgrade. I did the upgrade through the Update Manager. The reason I cannot load it from CD is because I don't have the ability to burn the program to a CD right now. 

Plus, I don't want the hassle of reloading something that's mostly working unless I can first do more to tell me that this small problem isn't far greater (which I highly doubt it is). 

I don't have (never have had) alsamixer or alsamixergui. I do have pulseaudio and rhythmbox. 

Is there something using the terminal I can check for?

---

### Post by mörgæs on 2010-05-12
One should always have at least one bootable device available. Some day it will be needed. 

I don't think that I can help any longer. An alternative boot will tell whether your machine does not like 10.04 in general, or whether something went wrong during the upgrade.

---

### Post by dino99 on 2010-05-12
> **CaronMargarete said:**
> Sorry I wasn't clear. Yes it technically is possible to boot from USB or CD because I have an ACER Aspire 4535, however I didn't boot from a CD originally, in fact never have with any upgrade. I did the upgrade through the Update Manager. The reason I cannot load it from CD is because I don't have the ability to burn the program to a CD right now. 

Plus, I don't want the hassle of reloading something that's mostly working unless I can first do more to tell me that this small problem isn't far greater (which I highly doubt it is). 

I don't have (never have had) alsamixer or alsamixergui. I do have pulseaudio and rhythmbox. 

Is there something using the terminal I can check for?

goto system-prefs-sound to see if your driver is activated

you need to install paprefs and gnome-alsamixer (tweak it as you need)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by CaronMargarete on 2010-05-12
> **dino99 said:**
> goto system-prefs-sound to see if your driver is activated

you need to install paprefs and gnome-alsamixer (tweak it as you need)

Dino99! Thank you! Super simple solution and I'm back to listening to my fav tunes! Brilliant!

---

### Post by CaronMargarete on 2010-05-26
> **CaronMargarete said:**
> Dino99! Thank you! Super simple solution and I'm back to listening to my fav tunes! Brilliant!

Spoke too soon. It works but every time I turn my laptop off it resets to no volume and I have to open the program and raise the control again. Annoying.
Is there a fix???

---

### Post by lifeframed on 2010-05-26
I have a similar issue.  I had installed 10.04 and everything was going fine.  Then there were some automatic updates.  I installed them and no sound.  There is a sound icon on the "system bar". If I select the sound the volume is 2/3rds the way up, but there are no bars of the volume icon.

---

### Post by lkjoel on 2010-06-21
Click [Fix your sound!]("https://help.ubuntu.com/community/OpenSound") on my sig. That should fix it.

---

