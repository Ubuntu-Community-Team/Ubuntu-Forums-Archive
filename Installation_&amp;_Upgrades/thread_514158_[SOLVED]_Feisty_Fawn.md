---
title: "[SOLVED] Feisty Fawn"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by Dave Otter on 2007-07-31
Ubgraded from Ubuntu 6.06 to 7.04.
     Lost sound 
      Have h ad to revert back to 6.06.
         Are there bugs in Feisty?

---

### Post by waggygee on 2007-08-02
> **Dave Otter said:**
> Ubgraded from Ubuntu 6.06 to 7.04.
     Lost sound 
      Have h ad to revert back to 6.06.
         Are there bugs in Feisty?

I haven't experienced bugs with my Feisty, Is there an audio driver present after the upgrade? I haven't upgraded my system before but maybe there was something that you did not do correctly.

---

### Post by Dave Otter on 2007-08-02
Yes -soundcard was recognised but but just kept switching off for no apparent reason!
    Does not happen on 6.06.

---

### Post by Seisen on 2007-08-02
How did you upgrade from dapper to feisty?

---

### Post by Dave Otter on 2007-08-03
I sent for a disc and did a clean install.

---

### Post by Seisen on 2007-08-03
Some people have had problems getting the sound to work in feisty, there is a post somewhere on here showed you how to fix your sound but I can't find it. If I do I will post the link here for you.

---

### Post by dabl on 2007-08-03
Ya, sound can be a little weird in Feisty.  Mainly folks find the default sound mixer has the mute set "on", for some strange reason.  ALSA seems to work better than OSS, so make sure you have the alsa-base, alsa-utils, and alsa-player packages installed. I get the alsamixergui as well.  Play with it a little, and it usually will come to life once stuff is unmuted. :)

---

