---
title: "Upgrade Problems"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by EricDallal on 2007-12-26
I recently upgraded from Edgy to Feisty and then to Gutsy. First, I had massive problems just getting intenet to work in Feisty. I also had some weird sound problems. The sound worked but there was weird distortion. When I listened to mp3s it sounded like it been recorded from a slightly out of tune radio station. Furthermore, the noise was there for every sound from every application, not just mp3s.

Now that I've upgraded to Gutsy, the problems are even worse. The internet disconnects and reconnects at at 11 second intervals (connected for 8 seconds, disconnected for 3 repeatedly). This pattern has been repeating for about 15 minutes now, since I restarted the computer.

Regarding the sound, I've changed the settings for the device to control to volume and it now works properly, except that the sound is extremely faint. I need to put both the manual knob on my computer and the sound control to full blast to hear anything at a reasonable sound level.

Does anybody have any idea how to solve these problems?

---

### Post by Pumalite on 2007-12-26
Go to Terminal and type:
alsamixer
Make sure all volumes are 100%

---

### Post by EricDallal on 2007-12-26
PCM is at 100. Master is at 0, but won't move. I'm guessing you don't want me to put Mic up and I don't know what the Caller I or off-hook do, but I can't put them off 0. None of them are on mute.

---

### Post by Pumalite on 2007-12-26
Maybe you should compile the latest alsa-driver (unless you already did it):

---

### Post by EricDallal on 2007-12-26
I already have the latest version of alsa-base. Are you saying I should download and compile the alsa-source package?

---

