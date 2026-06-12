---
title: "promise tx4310 sata raid support in fiesty fawn?"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by new2buntu on 2007-04-06
Hey folks-

I'm using a Promise TX4310 card for a SATA raid 5 array.  The logical drive is not recognized; I see 4 separate drives.  From searching this and other forums, **it seems this issue is well known.**  (Bolded just so those readers who like to skip lines will know this is not a repeat of the same question that's been asked many times.)

I've tried several suggested workarounds, and my understanding is the hiccup is with dmraid.  When it comes to Linux, I'm a light user; I'm not someone that can compile my own kernel and such.  **I do not want to use software raid.**  (Bold again for the same reason.)

I've had a machine built and ready to go for some time, patiently waiting for April 19th.  I didn't see any mention of "raid" in the blueprint for the pending release, however, and I'm not even sure this is something that falls under Ubuntu development.  My impression is that dmraid is developed as a larger part of the Linux community.

So, is there someone that can tell me whether support for this issue is coming in the near future, or do I need to give up and go back to Windows?  (No, *please* not *that*...)

Thanks,
Brock

---

### Post by 1ino1eum on 2007-04-06
hello.
I am in the same situation : I m using a Fakeraid0 with my new motherboard, and I havent been able to install ubuntu. I've try several workaround, but it never worked.
I concider myself as a quite good linux user, since I use linux for more then 5 years now, using debian, and gentoo. I managed to install gentoo on my raid0, and just had a boot problem but could fix it.
However I never been able to boot with a ubunt :/

I hope there will be a solution cause feisty looks really promising and really simple to use.

Finely, if there is no solution with ubuntu, I advice you, New2buntu, to try Fedora, where the instation on a Raid sysfem (even fakeraid with dmraid) is flawessly.

---

### Post by Niko_K on 2007-05-17
Same problem here...
.. i thought that the the tx4310 is supported in kernel 2.6.17 and above (in 2.6.17 there seemed to be a patch needed... but not in 2.6.18 and above)

I am now using 2.6.20 and debian 4.0... do i still need to compile the official promise driver? Shouldn't that work out-of-the-box??

---

