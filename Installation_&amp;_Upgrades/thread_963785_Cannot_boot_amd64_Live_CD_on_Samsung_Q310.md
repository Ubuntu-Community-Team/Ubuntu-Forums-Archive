---
title: "Cannot boot amd64 Live CD on Samsung Q310"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Jagot on 2008-10-30
Hi.

I'm trying to boot from the amd64 LiveCD on my Samsung Q310, but I'm having no luck.  As soon as the welcome screen is gone after I select 'Try Ubuntu without making any change to your computer', or whatever exactly it says, I simply get a black screen with a blinking cursor for about half a second, then it restarts my computer.  If I delete quiet splash from the boot options I get slightly further, but I can't tell on which line exactly it fails.

Thanks in advance if anyone can help.

---

### Post by SqdnGuns on 2008-10-30
> **Jagot said:**
> Hi.

I'm trying to boot from the amd64 LiveCD on my Samsung Q310, but I'm having no luck.  As soon as the welcome screen is gone after I select 'Try Ubuntu without making any change to your computer', or whatever exactly it says, I simply get a black screen with a blinking cursor for about have a second, then it restarts my computer.  If I delete quiet splash from the boot options I get slightly further, but I can't tell on which line exactly it fails.

Thanks in advance if anyone can help.


had the same problem, just let it set for about 15 minutes and then it loaded.

---

### Post by Pumalite on 2008-10-30
Try 'Safe Graphics Mode'.
If that doesn't work; download the amd64 Alternate CD.

---

### Post by Jagot on 2008-10-30
I have tried both safe graphics mode and the alternate cd but the same thing happens as with the live cd.

---

### Post by Pumalite on 2008-10-30
Next suspect is your burner. Clean the lens just in case.
If this is what you have:

Graphic Memory  	 256 MB GDDR3 (Ext. Graphic)
Graphic Processor 	nVIDIA GeForce Go 9200M GS (Ext. Graphic) 

It might be a problem.

---

### Post by Jagot on 2008-10-30
The burner wasn't the problem.  Tried burning discs on another couple of machines and same occurred.  Oddly, 32 bit Ubuntu seems to work fine for some reason.  Is there a problem with 64 bit Nvidia drivers?

---

