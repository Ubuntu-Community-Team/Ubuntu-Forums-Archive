---
title: "Nautilus broken after Hardy upgrade"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by noarc on 2008-04-22
```

$ nautilus
nautilus: symbol lookup error: nautilus: undefined symbol: eel_drect_empty

```

I have tried reinstalling all the libeel packages to no avail. These include libeel2-2, libeel2-data, and libeel2-dev.

---

### Post by Philk on 2008-04-22
Did you run the verification check on your CD you were installing from?

I don't know which version of Hardy you are using, but I had the 32-bit Gutsy and installed both 32- and 64-bit versions of Hardy.  I so like the 64-bit version that I am mainly using that now, but the Nautilus has no problem in my setup.

Good luck.

---

### Post by noarc on 2008-04-22
I upgraded from Gutsy using the update-manager.

---

### Post by Philk on 2008-04-23
Noarc,

Sorry you're having this problem.  Maybe one of the moderators could help you more than I can.

I can only tell you that I upgraded by downloading the release candidate, installing in a new partition, and had NO problems whatsoever.

I suggest you try the Synaptic Package Manager, go to the Nautilus entry there, and try a reinstall.  That might repair for you.

Again, good luck.

Phil

---

### Post by haytona on 2008-05-20
See here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/218321/comments/4](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/218321/comments/4)

I had a similar problem and needed to manually tweek some libeel2 symlinks.

---

