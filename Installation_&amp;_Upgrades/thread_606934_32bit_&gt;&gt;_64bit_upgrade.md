---
title: "32bit &gt;&gt; 64bit upgrade"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by Pevichaey5 on 2007-11-08
hi

i have decided to do an upgrade 2 64bit on my Core2Duo laptop

other than a backup of all my stuff (just completed) are tips from anyone? i read a similar post bout 7.04 32bit >> 7.10 64bit and saying it was possible.  is this true?

cheers

---

### Post by dabl on 2007-11-08
I would opt for the clean installation from the Alternate Install CD.  I haven't heard a firsthand report of an "upgrade" (really "conversion" would be more appropriate) from 32-bit to 64-bit.  Of course, that means your packages and settings will have to be done all over.  If you weren't changing architecture, the "Apt on CD" thing might help you -- maybe you can use that next time.

If you haven't done so before, you should put "/home" on its own partition separate from the rest of the OS.  If you did, then just make sure that you pick the same mount point and set it to NOT format that partition during the new installation.

I've been running 64-bit Gutsy Kubuntu for about 5 weeks, since the RC version was released.  There are still a few odd nitnoids with 64-bit, here are the ones I've noticed:

- Firefox -- can't install the player at rhapsody.com, and can't seem to get Java RE to install
- VMWare Player, ver. 1.something in the repos is broken
- K3b is broken (but it may be unrelated to 64-bit OS)(but brasero works fine)

The good news (for me) was that VMWare Player 2.0 has a 64-bit Debian download that installed and configured perfectly and flawlessly.

I hope this helps.  :)

---

### Post by Pevichaey5 on 2007-11-08
cheers

good help i'll follow your instructions then lol

---

