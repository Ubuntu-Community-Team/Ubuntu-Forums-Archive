---
title: "Any tips for soundcard upgrade in Feisty?"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by timzak on 2007-06-12
I'm thinking of disabling onboard sounds and putting in an old SB Live! (original) on my Feisty install.  Is there anything I need to know?  Will Feisty automatically detect the new soundcard on bootup and install drivers?  I just don't want to hose my system as I am a Linux newbie and have never done a hardware upgrade on an existing installation of any Linux OS.

Thanks in advance.

---

### Post by dannyboy79 on 2007-06-12
I can tell you that it's not going to HOSE your system up. As a side note, when being a newbie, it would beheave you to make backups of your entire system so that if you do ever screw up your system, you can always fix it. I use sbackup. It's got a gui and everything.

You'll want to make sure you disable the onboard sound card within your bios for less module confliction (module are/can be drivers within linux) Ubuntu should autodetect it and it should work. If not, you'll need to check out this guide: [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive)
BUT make sure it's not muted first, before you start any compiling of Alsa or anything drastic. 

May I ask why you want to switch sound cards anyway?

---

### Post by timzak on 2007-06-12
Thanks for the quick reply.

I use Partimage to back up my system, so I'm covered there.

Basically, support for my onboard sound is spotty.  It is Realtek HD audio 7.1.  Midi files do not play, there is no bass/treble control (this is a limitation of the onboard sound, not Feisty), and none of the "surround" effects work/have settings to control.

I have an SB Live! in another Feisty system (it was in there when I installed Feisty) and it seems to have much more robust support.  More options in the sound settings (bass/treble/surround effects).

There's no critical reason to change soundcards.  It's just a preference issue for me.

Do you see any reason why I should leave well enough alone?

Thanks.

---

### Post by dannyboy79 on 2007-06-12
well as you said, it's not well enough!!! ha ha ha. so yeah, go for the change. have you tried compiling alsa from source? just curious?

---

### Post by timzak on 2007-06-12
> **dannyboy79 said:**
> well as you said, it's not well enough!!! ha ha ha. so yeah, go for the change. have you tried compiling alsa from source? just curious?

No, I haven't.  I'm not even sure what that means.  It sounds like programing the sound drivers from scratch.  It can't be that difficult to change a sound card, can it?  LOL.

---

### Post by dannyboy79 on 2007-06-13
no, you're right, inserting a new PCI sound card is easier than compiling new alsa driver's from source but  it  was only a suggesiton. good luck

---

### Post by timzak on 2007-06-13
Just out of curiosity, under what circumstances would one want/need to compile Alsa from the source?  What does it mean, exactly, to compile from the source?

Thanks for your feedback.

---

