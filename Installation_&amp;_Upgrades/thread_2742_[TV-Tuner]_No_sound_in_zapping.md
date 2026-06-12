---
title: "[TV-Tuner] No sound in zapping"
date: 2004-10-31
forum: Installation &amp; Upgrades
---

### Post by HiddenWolf on 2004-10-31
When I went on trying to get my PCTV Rave going, I was pleasantly suprized that it already did. To be honest I get more channels then with the software Pinnacle supplied with the card.

However I can't seem to get sound working. The card forwards it to the line-in of the soundcard, but opening the line-in in alsa-mixer-gui does nothing.
The soundcard is an Audigy.

Is there anything I need to install to get sound?
What are the correct settings for zapping?

---

### Post by emperor on 2004-10-31
Have you tried tvtime just to see if that works! I had a similar problem with sound with tvtime and my tuner card. However I was able to fix the problem by setting the input line from the mixer. In my case, the input was line1, for example:
  
  tvtime --mixer=/dev/mixer:line1
 
 This worked on my SB Live card and should work with your Audigy card. 
 
 Zapping may also have a similar cmdline option for setting the mixer correctly.

---

### Post by HiddenWolf on 2004-10-31
Tv-time is a lot better. Zapping is gone. Woohoo.

Yeah, I've got sound now. Alsa muted the input, which I hadn't noticed.

---

