---
title: "2nd processor detected?"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by surfer69 on 2007-10-21
I just won a dual Xeon processor server on ebay, but it only has one processor fitted.
Question is... if I install Ubuntu server with just one processor in it, will Ubuntu detect and use the 2nd processor automatically after I insert it, or would I need to re-install?

I'd probably do it for the practice anyway.

---

### Post by ezak on 2007-10-21
You most definitely got a Dual Core Xeon processor, so that means it has "2 cores" instead of actually being 2 physical processors it has 2 cores on one chip. And to answer the main question, yes Ubuntu Server should most likely recognize both cores out of the box as long as you have installed the right kernel for it.

---

### Post by surfer69 on 2007-10-22
> **ezak said:**
> You most definitely got a Dual Core Xeon processor
Do you mean definitely or probably?

No, it is a Supermicro dual Xeon SuperServer - it has one Xeon fitted at the moiment and one socket ready for another processor.

At the moment I'm running Windows Server 2003 Enterprise version on a Delll Netfinity Server with 2 (two) 1Ghz Xeon processors and this one is to replace it, I need the room! Its network name is Harrypotter 'cos it's living under the stairs.

---

### Post by ezak on 2007-10-22
Oh, I must have read wrong, I didn't see 'server" in there heheh. 

In that case then yes, as long as the CPU is the exact same model and speed/type as the other of course, it will detect and run both the CPU's without a problem. But you also have to keep in mind you need the correct kernel installed and present to load upon boot.

No re-installation needed :)

(You can completely ignore the previous reply by me!)

---

