---
title: "sound card ess allergo(es1988)"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by buffalohuck on 2005-09-09
I know that this sound card(ess allergo) don't work well with linux,but I can't get it to even boot on install or live disk.Which linux would work with this sound card or how do I make this sound card work ???

---

### Post by wvslkr on 2005-09-10
Your card is supposed to work with the maestro3 driver.  

Open a terminal and type > sudo modprobe snd-maestro3 

If no errors are spit back at you it has probably loaded the card.  You may have to play around with some of the sound settings to get it to work.  If problems do a search on sound,  there are lots of threads.

If it works add:    snd-maestro3       to /etc/modules with your favorite text editor.  This will make it work from boot-up.

GL :)

---

