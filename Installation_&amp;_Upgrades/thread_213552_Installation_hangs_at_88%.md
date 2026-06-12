---
title: "Installation hangs at 88%"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by bpasdar on 2006-07-11
I have a system with an intel motherboard and 3 SATA drives (two on a 3ware controller card and one on the motherboard).

I am try to install with kubuntu-6.06-i386 Desktop and it boots just fine to the live CD, however when installing to the system the installation hangs at 88% everytime.

Using an older Breezy installer works OK, but I would like to install with Dapper.

Any suggestions?

Babak

---

### Post by GavinC on 2006-07-11
Ours is hanging at 15%, using the ubuntu (no "K") desktop installer, on a fairly standard HP box. Now trying again with the alternate CD rather than the desktop one, will let you know how we get on.

Gavin

---

### Post by DavidFL on 2006-07-11
My Ubuntu install hung at 58% the first time I tried it although the Live Cd worked great.  I then ran the CD check and it reported a mismatch on the squashfs.  I simply took out the CD gently cleaned it. Blew on it a few times.  Tapped it three times and said some magic words and tried again.  It worked like a charm. :)  You may wish to just try a second time.  I suspect that in some instances data is not being read from the CD or written to the Hard disk correctly for whatever reason.  Obviously if the problem is the disk itself, this won't help though.  Worth a shot anyway.

---

### Post by GavinC on 2006-07-12
Now working, used the alternate CD. Probably won't bother with the graphical installer from now on.

Steps added to our install procedure:

1) Use the "Check CD" option from the menu before installing.
2) Use the "Test Memory" option as well.

Gavin

---

### Post by kmouts on 2007-02-08
I have exactly the same problem, stopping at 88% with a Kubuntu 6.06.1 LTS Dapper Live CD.
When I run a CD check, it found "squashfs mismatch".
I will try to get the alternative installation instead.

---

