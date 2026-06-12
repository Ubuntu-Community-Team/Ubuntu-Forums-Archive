---
title: "grub issue, ubuntu wont load"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by spewperb on 2007-06-01
I have just dual booted ubuntu and windows xp. Windows boots up correctly however when I try to boot into ubuntu, all I get is the word grub and a flashing underscore. The only thing that works is ctrl alt del which reboots the system. Any idea's??

---

### Post by merlinus on 2007-06-01
Try this, in a terminal:

```

sudo grub
find boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

Substitute your results from find in root and setup.

-merlin

---

### Post by spewperb on 2007-06-01
How do I access terminal. With the live cd?

---

### Post by merlinus on 2007-06-01
Yes, once the live cd is up-and-running.

-merlin

---

### Post by spewperb on 2007-06-04
I still cant get ubuntu to load. Can I just check that I'm installing grub to the correct place. I have four partitions

hd1 - NTFS (Windows XP)
hd2 - ex3 (Ubuntu)
hd3 - Linux swap
hd4 - Fat 32 (Shared Space)

No when I come to the bit about grub in the linux installation, its default it (hd0). Should I be changing this to (hd1)?

Please help. This has been bugging me for ages!

---

### Post by confused57 on 2007-06-04
You might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You definitely want to install grub to (hd0)...the SGD should be able to boot your Ubuntu.

---

### Post by Masonba2000 on 2007-06-05
The fastest way to do it, and the easiest (5 steps) is using SGD. Tutorial here, [http://thejist.info/?p=109](http://thejist.info/?p=109)

---

### Post by DJiNN on 2007-06-05
> **Masonba2000 said:**
> The fastest way to do it, and the easiest (5 steps) is using SGD. Tutorial here, [http://thejist.info/?p=109](http://thejist.info/?p=109)

Hey, just wanted to say "Great Web site" and i love the review of "The Fountain". Really well written, succinct & to the point but full & thoughtful. Way to go..... :)

DJiNN

---

