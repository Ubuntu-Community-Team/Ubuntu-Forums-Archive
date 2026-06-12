---
title: "Installation error (ACPI: Resource is not an IRQ Entry...)"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by dozey on 2007-05-10
Hi,

**On first installation...**
Downloaded the ubuntu-7.04-server-i386.iso
Burnt to disk.
**Booted...**
Selected top menu option to install...
Few seconds later...

**Errors:**
[0.130189] ACPI: Resource is not an IRQ Entry
[0.143455] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP040

**System:**
HP Netserver E800
Dual Pentium933
786 Meg Ram
2 x 9 gig SCSII HD


If there is any one out there that knows how I can sort this out so that I can install 

Thanks!
Brad

---

### Post by mrbillbob on 2008-01-13
I have just recently had the same issue with the E800.  Have you been able to resolve the issue?

Thanks in advance.

---

### Post by theJagger on 2008-03-19
i have gotten  bit further with the alternate install cds. When the boot menu comes up i hit F6. then i remove>  quiet -- and add > noacpi nolacpi acpi=off with that i get a bit further. though i have not been able to get any ubuntu running on the e800 netserver so far. I hope i remember to post back if i do get this working...

---

### Post by CRAK on 2008-04-07
If it's of any help:
I had exactly the same issue when installing 7.10 in my E800. On both the client and the server install did.
An old (from 2003) Knoppix release did boot. A recent version (5.1) did not.
Knowing nothing about Linux (yet) I assumed a driver issue, related to older hardware, so I went back in time on Ubuntu LAMP as well: 6.06 "Dapper Drake".
That did the job!

---

### Post by MonsterTrimble on 2008-05-02
I run a netserver E60 (Dual P3-550s) as my home server. I have had success installing Fluxbuntu 7.10 and then installing whatever server-worthy desktop on top of it.

I also just tried installing Xubuntu 8.04 Alternate (due to my 7.10 install tanking) and I had a kernel panic. Obviously I suspect that the older kernel Fluxbuntu uses is the key, although I have tried 6.10 with no success.

Have you tried 5.10? Maybe the kernal is old enough? Personally I'm thinking of just installing old-school Debian and upgrading. I know I have upgraded the kernel with no issues - it's just with the install.

---

