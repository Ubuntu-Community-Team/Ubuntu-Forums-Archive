---
title: "installation problem with PCI Interrupt"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by hwl on 2007-10-25
Boot hangs with the last dmesg as
ACPI : PCI Interrupt Link [LNKC] enabled at IRQ11
ACPI : PCI Interrupt 0000:00:0a.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11

The machine is IBM Thinkpad X21. 
Tried boot options:
acpi=off, noapic, nolapic, etc.  but didn't work.  

The machine works fine with Windows XP,  so it shouldn't be hardware problem.  

The machine used to work fine with 6.06LT, but after I install 7.04, it hangs afterwards.  7.10 doesn't help either.  

Would appreciate if anyone can help.


--------------------------------------------------------------------------------------------------

After another day investigation.  

I tried redhat 9, 8, 7.3, 7.2, and then finally successfully boot up the system with redhat 7

During redhat 9, 8, and 7.3/7.2 installation, they all showed and hanged:

PCI: Found IRQ 11 for device 00:0a.1
PCI: Sharing IRQ 11 with 00:0a.0
Redundant entry in serial PCI_table. 
Please send the output of 
lspci -vv, this message (11c1, 045C, 8086, 2205) and 
the manufacturer and name of serial board or modem board to [email]serial-PCI-info@lists,sourceforge.net[/email]

After I boot up with redhat 7, lspci command showed output
 00:0a.0 as Ethernet Controller, INTEL 82557 (Ethernet Pro 100) rev.0c
 00:0a.1 as Serial Controller, Lucent Microelectronics unknow device 045c (rev 01)

I tried to boot up the system with Ubuntu 6.06LT with PCI3 (ethernet/modem combo card) disabled, but the kernel still hanged as before. 


I remember that this syndrome happened after I boot up my working 6.06LT, then after a kernel update, the system never boot up again thereafter.

I wonder if recent versions of kernel won't support the combo card anymore.  Is there anyway to work around the problem?  

Thanks in advance for any advice.

---

### Post by hwl on 2007-10-26
update new foundout.

---

### Post by photohikaru on 2007-10-26
I'm sorry, what does that mean?


> **hwl said:**
> update new foundout.

---

### Post by gwhit918 on 2007-10-30
I'd be interested in any insight into this problem.  My Thinkpad T21 is hanging with the same messages as reported by the original poster.  I tried the same boot options and more, to no avail.

---

### Post by willingc on 2007-10-31
Have you tried nosplash as a boot option?  This along with the acpi apm options worked for me.  Good luck.

I have 7.10 working on a T21.  This upgrade (from 7.04) was a little less smooth than other upgrades.  Some issues with the PCI message and video.  I wish I had written down the specific video steps that I used to get it working.  I did use tips from this forum (searching on T21, T22, savage).

---

