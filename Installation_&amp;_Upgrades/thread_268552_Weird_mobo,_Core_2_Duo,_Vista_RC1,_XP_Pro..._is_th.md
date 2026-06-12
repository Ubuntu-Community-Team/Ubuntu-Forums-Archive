---
title: "Weird mobo, Core 2 Duo, Vista RC1, XP Pro... is there room for ubuntu?"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by Sirron on 2006-09-30
I've been running ubuntu on my laptop for a while (I actually bought it for that purpose) but I miss it on my desktop now.

My desktop has a Core 2 Duo CPU, and the motherboard is an Abit AB9 Pro. The motherboard is pretty weird, it's got 9 internal SATA ports, one external sata port and only one IDE port - which is for some reason connected to a chipset made by JMicron, not directly connected to the intel chipset. There's the JMicron chipset, a Silicon Image one (or something) and the Intel P965 one.

It has Windows Vista RC1 and XP Pro SP2 installed. Vista is on an 80GB SATA2 hard drive, XP is on a 300GB SATA hard drive. They're both connected to the Intel SATA ports.

Would getting ubuntu to install somewhere on the 300 gig without screwing up Vista (which I am deeply in love with sorry) or XP (which I despise but need until Vista has better support) be as nightmarish as it sounds? It won't even boot from the Live CD at the moment - probably because even Vista's setup needed a floppy disk with drivers on for the Jmicron chipset.

---

### Post by pay on 2006-09-30
You can easily shrink that XP drive to make space for Ubuntu (atleast 5gb). As with booting the liveCD you could try the altenate install cd which installs in a text based environment.

---

### Post by Sirron on 2006-10-01
Thanks, but I think I'll leave my desktop for now, and see whether the next release of ubuntu will boot from the Live CD.

---

### Post by xelink on 2006-10-15
975x and 965 dropped legacy support for PATA, aparently intel thinks that people don't use pATA anymore...

ALL x2d boards are like this(unless you count 845 boards but who wants to run a c2d at 800mhz FSB when they can run it at 1600 for a 50% overclock)

---

### Post by Sirron on 2006-10-19
Oh right, ok, that makes sense

IDE cables are awkward anyway, hopefully now we'll start seeing more SATA optical drives

---

