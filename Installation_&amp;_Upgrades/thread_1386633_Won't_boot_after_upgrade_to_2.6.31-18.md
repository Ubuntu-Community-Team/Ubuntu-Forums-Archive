---
title: "Won't boot after upgrade to 2.6.31-18"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by bexpert on 2010-01-20
I ran the recommended update to my Eee 1005HA with 9.10. I believe I upgraded to kernel 2.6.31-18. 

Now my computer won't boot into -18, though it will still boot into -16 and Windows XP. 

(I'm really fed up with Ubuntu. First, I spent ages trying to get my wireless to work at full speed (again, a stupid 'upgrade' ruined it), and now this. Is it too much to ask that upgrades don't make things worse? Seriously?)

Any idea how to get this to work?

---

### Post by kutya61 on 2010-01-21
Do you get any error messages when booting in -18?

---

### Post by Leppie on 2010-01-21
> **bexpert said:**
> I ran the recommended update to my Eee 1005HA with 9.10. I believe I upgraded to kernel 2.6.31-18.
i don't think that was a recommended upgrade, just ran update manager and my kernel is version 17. i think you have the "proposed" or "backports" repo enabled (or both). they both push test updates through. check your sources in System>Administration>Software Sources, go to the updates tab and make sure only the 1st two options are ticked.

> **bexpert said:**
> (I'm really fed up with Ubuntu. First, I spent ages trying to get my wireless to work at full speed (again, a stupid 'upgrade' ruined it), and now this. Is it too much to ask that upgrades don't make things worse? Seriously?)
choosing to have all kinds of updates (stable, pre-release and testing) installed probably isn't the way to go if this is the first time you installed ubuntu.

boot into your system with the 16 kernel, check the software sources list, then in synaptic remove the 18 kernel. after that you could run update manager to have the 17 kernel installed.

---

### Post by darkod on 2010-01-21
> **Leppie said:**
> i don't think that was a recommended upgrade, just ran update manager and my kernel is version 17. i think you have the "proposed" or "backports" repo enabled (or both). they both push test updates through. check your sources in System>Administration>Software Sources, go to the updates tab and make sure only the 1st two options are ticked.


choosing to have all kinds of updates (stable, pre-release and testing) installed probably isn't the way to go if this is the first time you installed ubuntu.

boot into your system with the 16 kernel, check the software sources list, then in synaptic remove the 18 kernel. after that you could run update manager to have the 17 kernel installed.

I am also on -17 so I don't know about this -18 kernel (unless it's a typo). And for reference, I didn't spend that long to make my new usb N wi-fi work in Karmic, and that was on -14. All subsequent kernels, -15, -16 and -17 are working OK with it without any need to redo anything again.
And Karmic is my first ubuntu, also for the record. Never seen ubuntu before it.

---

