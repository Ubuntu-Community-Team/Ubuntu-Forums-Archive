---
title: "Soundless Auidgy 2?"
date: 2004-10-29
forum: Installation &amp; Upgrades
---

### Post by zetamannsky on 2004-10-29
I have  no sound from my Audigy 2 card. However, the Creative Open Source site states that the Audigy 2 card is supported by the Emu10k1 or ALSA driver in linux, which, I understand, is part of the ubuntu final release 4.10. Why is it, then, that I can not get sound on my system eventhough my Audigy 2 is recognized? Can someone please help me to configure this card?

---

### Post by Joeb on 2004-10-29
[QUOTE=zetamannsky]I have  no sound from my Audigy 2 card. However, the Creative Open Source site states that the Audigy 2 card is supported by the Emu10k1 or ALSA driver in linux, which, I understand, is part of the ubuntu final release 4.10. Why is it, then, that I can not get sound on my system eventhough my Audigy 2 is recognized? Can someone please help me to configure this card?[/QUOTE]

I just have a SBLive card, but I know that several of the volume controls were set to the minimums in the mixer.  Have you checked them?

Joeb

---

### Post by FLeiXiuS on 2004-10-29
I may reccommend that you do check the mixers.  If not then try this..

```
sudo modprobe emu10k1
```

Then check your mixers again.

---

### Post by zetamannsky on 2004-10-30
I still have no sound from my Audigy 2 card after doing the following. I have checked my mixer. There are two major tabs: OSS Mixer and the ALSA Mixer. They all have their controls set, at least, in the middle. All the locked options are chosen and no mute is chosen. There were many repetitons of "Emu10k1 PCM Send" and "Emu10k1 PCM send Routing". A couple times the mixer crashed when I tried to set the controls to the middle. All this was done after I ran "sudo modprobe emu10k1". I am using the CD Player to test for sound. But still I have no sound. Please help.

---

### Post by Joeb on 2004-10-30
Do you have no sound at all (for instance, startup music) or just no sound from the CD player?

---

### Post by zetamannsky on 2004-10-30
Yes, I have sound when the system begins (start up music) but it is very low. But I have no sound from either the CD Player or Xmms.

---

### Post by FLeiXiuS on 2004-10-30
[QUOTE=zetamannsky]Yes, I have sound when the system begins (start up music) but it is very low. But I have no sound from either the CD Player or Xmms.[/QUOTE]


Configure which sound mixers they use.  For example, I have installed OSS and ALSA drivers.  I run XMMS on ALSA and SYS on OSS.  Just no reason at all..  Just be sure that the mixers are correctly set.

---

### Post by zetamannsky on 2004-10-31
[QUOTE=FLeiXiuS]Configure which sound mixers they use.  For example, I have installed OSS and ALSA drivers.  I run XMMS on ALSA and SYS on OSS.  Just no reason at all..  Just be sure that the mixers are correctly set.[/QUOTE]


How do I know which mixer controls which application? You tell me to set each mixer correctly. What are the correct settings for each mixer? As far as I know they are similar to the way they are in my Win XP system, in which sound works beautifully. In ubuntu, I only have sound from the startup music  and at system events but no sound from any other application such as the CD Player. I am one frustrated newbie! Please help.

---

