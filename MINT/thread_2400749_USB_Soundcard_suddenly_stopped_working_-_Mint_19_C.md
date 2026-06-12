---
title: "USB Soundcard suddenly stopped working - Mint 19 Cinnamon"
date: 2018-09-09
forum: MINT
---

### Post by cowardlybattlecat on 2018-09-09
Hello, all,

I recently installed linux Mint 19 on my system with Windows 10 on a different disk.

My sound had been working and then exactly this occurred:

[https://ubuntuforums.org/showthread.php?t=2263276](https://ubuntuforums.org/showthread.php?t=2263276)

My experience matches that of the first two posts in that thread precisely.

I went to see about making the max volume louder somehow (everything works fine and at higher volume in Windows).  When I quickly clicked on one of the other output options, the ability to select my headphones disappeared from the sound settings panel.

When I opened alsamixer in terminal, I was able to press F6 to see the list of sound cards, including mine as sound card 2.  Selecting it closes alsamixer and gives the following in terminal:

```
cannot load mixer controls: Invalid argument
```

I installed qasmixer based on a suggestion found online.  When I select mixer device "hw: card" then my card from the list, I get:

"
**Mixer device couldn't be opened**
**Function:** snd_mixer_load
**Address:** hw:CARD=2
**Error:** Invalid argument
"

Details:
headphones are Steelseries Siberia 650, which come with their own external sound card (these: [https://steelseries.com/gaming-headsets/siberia-650](https://steelseries.com/gaming-headsets/siberia-650) )

Seems like my system recognizes the card/headphones are there, but something is missing/got deleted such that alsamixer/qasmixer/sound settings can't select the sound card.

I pretty confused and not certain how to fix it.  I have tried quite a few things, so I'm not certain which to describe here.  I would have necro-posted on the linked thread, but it's closed.  As far as I can tell, those two users had precisely the same issue I have now.

I'm not even certain if this is the correct forum since I am a Mint user (not exactly ubuntu but based on it), but the given that the problem is _precisely_ what was described by the folks in the thread, I figured I would give it a shot. Any help is greatly appreciated!

---

### Post by wildmanne39 on 2018-09-09
*Thread moved to **MINT for a more appropriate fit**.*

---

### Post by cowardlybattlecat on 2018-09-11
I marked the thread as solved.

Here is the solution that worked to solve my primary problem.

[https://forums.linuxmint.com/viewtopic.php?t=134232](https://forums.linuxmint.com/viewtopic.php?t=134232)

As detailed in the linked thread, qasmixer and alsamixer still can't access any sort of config for the card, but the sound is working.

---

