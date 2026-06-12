---
title: "Wireless Driver For EEE 1005HA-P?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by popejeremy on 2009-10-03
I'm running Karmic on my Asus EEE 1005HA-P, and wifi reception seems a bit flaky sometimes. Is there perhaps a special driver somewhere that I should be using instead of whatever came with Ubuntu Netbook Remix? If so, how can I get it? Thanks!

---

### Post by t.alex on 2009-10-04
are you using an Atheros chip? n draft?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560)

ath9k is a total mess in 2.6.31 :(

---

### Post by popejeremy on 2009-10-04
> **t.alex said:**
> are you using an Atheros chip? n draft?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560)

ath9k is a total mess in 2.6.31 :(

Yes, I am. Damn, that bug-page looks like a mess.

---

### Post by tophatandy on 2009-10-06
> **popejeremy said:**
> I'm running Karmic on my Asus EEE 1005HA-P, and wifi reception seems a bit flaky sometimes. Is there perhaps a special driver somewhere that I should be using instead of whatever came with Ubuntu Netbook Remix? If so, how can I get it? Thanks!

same computer, i just did a fresh install of karmic about two days ago, and everything is working fine besides when i close my laptop or let it go to sleep i begin to get terrible wifi reception. 

I have found that closing the laptop and opening it back up helps sometimes, or what has always worked for me is a soft reboot. (ik. its not a fix, but its the best that can be done right now with ath9k such a mess).

give it a try next time the reception sucks. post the results.

---

