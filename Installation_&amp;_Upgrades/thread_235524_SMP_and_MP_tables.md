---
title: "SMP and MP tables"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by 1an on 2006-08-13
Whe trying to boot from live cd (in order to install) I get: 

[4294667.296000]  SMP mptable: null local APIC address!
[4294667.296000]  BIOS bug, MP table errors detected...
[4294667.296000]  diasabling SMP support. (Tell your hw vendor)

Any thoughts?  I've tried "live acpi=off" and "noapic".  Neither worked.


I'm using a P4 1.4G processor with 384Mb of RIMM.  This is a Dell Dimension 8100.

---

### Post by 1an on 2006-08-13
Ok, here's the full version of it::

Using Live CD (ubuntu-6.06.1-desktop-i386.iso)
Boot up
Error Message Below Displays
	[4294667.296000]  SMP mptable: null local APIC address!
	[4294667.296000]  BIOS bug, MP table errors detected...
	[4294667.296000]  diasabling SMP support. (Tell your hw vendor)
Ubuntu logo displays
	Loading Essntial Drivers....ok
	Mounting Root File System....ok
	Moving Mount Points....ok
	Adding Live CD User.... (screen changes w/o displaying ok)
Error Message Below Displays
	[4294667.296000]  SMP mptable: null local APIC address!
	[4294667.296000]  BIOS bug, MP table errors detected...
	[4294667.296000]  diasabling SMP support. (Tell your hw vendor)
System hangs indefinately


This is on a P4 1.4G, with 384MB of RIMM, using a Maxtor 40G HD, and a Sony CD R/w (52x/24x/52x).  Dell Dimension 8100

---

### Post by clyde9999 on 2006-10-23
I also have a Dell Dimention 8100 with the exact same problems, however, I have found that Fedora Core 5 runs on it just fine, I also have not had any problems in the past with Kubuntu runnung on it. Fedora Core is on it at the present. I do get the errors on bootup, but it does not stop it from booting. Maybe you can give Fedora a try and see if it works on your system.

---

### Post by christhemonkey on 2006-10-23
You could try booting with the parameters:
```
noapic nolapic 
```
That should avoid trying to use the buggy apic implentation.

---

