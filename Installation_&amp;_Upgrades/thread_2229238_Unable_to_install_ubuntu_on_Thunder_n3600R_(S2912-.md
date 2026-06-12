---
title: "Unable to install ubuntu on Thunder n3600R (S2912-E)"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by MSPdwalt on 2014-06-12
I'm having issues installing Ubuntu Server 14.04 on a server with a Thunder n3600R (S2912-E) mobo.  Both the server DVD and the live DVD fail right after the splash screen. I've tried nomodset, minimal install, a 14.04 live CD, 12.04.  Anyone else have an issue with this board? Is there a way I can run it in text mode? or at least get it to throw me something diagnostically relevent?  I should be more clear, by fail I mean black screen.

---

### Post by derekm2 on 2014-08-09
> **MSPdwalt said:**
> I'm having issues installing Ubuntu Server 14.04 on a server with a Thunder n3600R (S2912-E) mobo.  Both the server DVD and the live DVD fail right after the splash screen. I've tried nomodset, minimal install, a 14.04 live CD, 12.04.  Anyone else have an issue with this board? Is there a way I can run it in text mode? or at least get it to throw me something diagnostically relevent?  I should be more clear, by fail I mean black screen.

Had the same problem with Opensuse 12.3 .. its working now

first make sure your bios is version 5.01
two : in the bios set O/S to other
three : iopage to not shadowed
Disable ACPIMCFG tables in the power page

---

