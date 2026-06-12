---
title: "Gutsy boot hangs while starting services"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by jjgg123 on 2007-10-20
Hi all,

I just upgraded to Gutsy from Feisty, and now I can't boot.  I get the Ubuntu splash screen, and the orange progress bar goes all the way to the end, then the screen goes black and shows a bunch of British pound signs across the top line of the screen.  This alternates with a blank screen a few times, and then ultimately, the top line shows:

* Starting OpenBSD Secure Shell server sshd           [ OK ]

and then the system hangs.


I tried booting in recovery mode, which shows a lot more information while booting, but ultimately it still hangs with the top line showing:

* CPU frequency scaling not supported


Has anybody seen this behavior, or have some ideas as to what the problem might be?

My hardware is somewhat unusual (a year-old Via mini-ITX board with Via CPU), but I've been running Feisty on this system for months, so I don't think there is a basic hardware incompatibility.

Any help would be greatly appreciated.

Thanks!

Jeff

---

### Post by mfblankenstein on 2007-10-20
I have the same problem. Older PC, but not an unusual one. It was running Fiesty Fawn just fine as with all previous versions of Ubuntu. Now it won't boot. This is not a good sign!

---

### Post by mfblankenstein on 2007-10-20
It dumps me into Busybox v1.1.3 at the initramfs) prompt. What am I supposed to enter here to run graphic mode? Thanks in advance...

---

### Post by deadite66 on 2007-10-20
> **mfblankenstein said:**
> It dumps me into Busybox v1.1.3 at the initramfs) prompt. What am I supposed to enter here to run graphic mode? Thanks in advance...

i get that a lot too, only 1/5 boot gets me a working system.

---

