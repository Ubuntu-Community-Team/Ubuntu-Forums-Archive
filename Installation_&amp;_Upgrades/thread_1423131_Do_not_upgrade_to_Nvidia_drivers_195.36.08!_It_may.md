---
title: "Do not upgrade to Nvidia drivers 195.36.08! It may fry your vide card!"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by gradinaruvasile on 2010-03-06
I post a link to the discussion on the Lucid Lynx section, but this serious issue affects all who use the above mentioned driver versions, regardless of ubuntu version:

[http://ubuntuforums.org/showthread.php?t=1422970](http://ubuntuforums.org/showthread.php?t=1422970)

I did some googling as i too used the 195.36.08 drivers:

- Some Windows users have reported fried video cards with the driver 196.75, related to fans that stopped working - due, it seems, to a bug in the drivers automatic fan profile handling or something like that. The fan did not start at all, although it should have when the card reaches a preset
temperature - the cards literally fried. In the accounts i saw were high end cards (8800 and the like) used for gaming as far as observed.

That driver version seemingly has the same changes that the Linux 195.36.08 version. 

The nvidia devs pulled the 195.36.03 and 195.36.08 drivers from the download site and advise all who has installed these drivers to use the 190.53 or 195.30 drivers instead.

---

### Post by URGettingADull on 2010-03-06
Dammit!  I just installed that one, it is the only one, as far as I know, that can actually make my card run in its enhanced performance mode (9800GT).

Thanks for the warning, will be downgrading to 190.xx

---

### Post by gradinaruvasile on 2010-03-06
> **URGettingADull said:**
> Dammit!  I just installed that one, it is the only one, as far as I know, that can actually make my card run in its enhanced performance mode (9800GT).

Thanks for the warning, will be downgrading to 190.xx

195.30 should be enough.

BTW: I didnt hear of these problems on linux, but better be safe than sorry. I too downgraded to 195.30 (except on one computer with an integrated fanless 8200).

---

### Post by URGettingADull on 2010-03-06
I didn't see an x86 195.xx driver, the only one listed on nvidia's site is the 190.53...

---

