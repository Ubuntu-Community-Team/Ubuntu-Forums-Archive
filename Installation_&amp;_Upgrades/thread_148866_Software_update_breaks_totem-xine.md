---
title: "Software update breaks totem-xine"
date: 2006-03-22
forum: Installation &amp; Upgrades
---

### Post by wmcbrine on 2006-03-22
Not sure where to post this... and perhaps "break" is too strong a word. But a recent automatic update (I'm on Breezy 64 BTW) left a warning that the totem package could not be upgraded; and the warning kept coming up with every subsequent update. The only way to get rid of it was to change from totem-xine to totem-gstreamer in Synaptic, and upgrade that. Weird, but no problem, I thought; I'd just switch back when it was done. But there *was* a problem: If I reselect totem-xine now, I have to uninstall the "totem" package; and if I remove *that*, I have to remove ubuntu-desktop! If I do all that, and then try to reinstall totem, it insists on removing totem-xine again. It seems the "totem" psuedo-package now only depends on totem-gstreamer. :(

I couldn't find any discussion of this via the Search box, but I can't be the only one affected?

Since I'd switched, I did try sticking with totem-gstreamer for a few minutes; but it still doesn't play DVDs.

---

### Post by Zimmer on 2006-03-24
I am glad I just ignored the message (it is still showing when Updates come in)  and left totem well alone. It is still working...  a bit of a mystery....
The answer could lie in the version numbers. totem-xine is still 3 and the rest are 3.1
You may have to re install totem-xine by using the 'force version' option, but that is JUST a guess..you may need to ask a real expert on this...I am leaving my totem well alone for the time  being, as the instructions that came with the update were very obscure..

---

### Post by Greeface on 2006-04-02
I have the same problem, and it screws up most of my videos, not only DVDs.  I'll be sure to post back if I find a solution.

---

### Post by Greeface on 2006-04-02
Ah ha! Zimmer was right, select Totem in synaptic and downgrade it until it says that its gonna remove totem-gstreamer and install totem-xine.

Thanks Zimmer

---

### Post by Tomas_B on 2006-04-16
THANK YOU!!! 
I was going crazy trying to figure this one out.

After downgrading delete your ~/.thumbnails to get the thumbnails back :-)

I love totem-xine and it's nice to have it back in a working condition

---

