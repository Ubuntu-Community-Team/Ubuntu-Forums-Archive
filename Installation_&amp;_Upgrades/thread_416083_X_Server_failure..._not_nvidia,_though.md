---
title: "X Server failure... not nvidia, though?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by MsTiggy on 2007-04-20
I read that some other people have had the X server failure because of the nvidia changing to nv thing, but I went through my xorg.conf file, and there isn't nvidia anywhere (I don't remember having it, either).

So what I need to figure out is what my problem is.

When I view the details it offers me, at the very end it says this:

```
(--) Assigning device section with no busID to primary device
(EE) No devices detected.
Fatal server error:
no screens found
```

I'm completely at a loss.  Any suggestions?

---

### Post by taurus on 2007-04-20
Do you have two graphic cards, one onboard and one add on?  Otherwise, boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by MsTiggy on 2007-04-20
No, I don't have 2 cards.

How do I boot into recovery mode?

---

### Post by anachreon_ on 2007-04-20
MsTiggy, you should have an option on your GRUB boot loader to load ubuntu (safe mode), right?  Can you select that and try taurus's recommendation?

---

### Post by MsTiggy on 2007-04-20
Yay!  It worked!  I ran what taurus said in recovery mode, selected the correct device, and now it's up and running!  Thanks!

---

