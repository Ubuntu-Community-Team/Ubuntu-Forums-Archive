---
title: "[SOLVED] Recompiling 2.6.24-22 kernel"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by gatenby_jp on 2008-08-23
I think I have screwed up my 2.6.24.19 kernel. 

I installed a Edimax ew-7128G WIFI card ... which did not appear to run out of the box. So I downloaded Ralink Driver and compiled the R61 module. The card then seemed to work after a fashion but not well.

I rebooted using the 2.6.22-15 kernel and the card works properly.

Is there any harm in leaving the machine booting on the older kernel or should I recompile the 2.6.24-22 kernel and if so how?

---

### Post by gatenby_jp on 2008-08-23
> **gatenby_jp said:**
> I think I have screwed up my 2.6.24.19 kernel. 

I installed a Edimax ew-7128G WIFI card ... which did not appear to run out of the box. So I downloaded Ralink Driver and compiled the R61 module. The card then seemed to work after a fashion but not well.

I rebooted using the 2.6.22-15 kernel and the card works properly.

Is there any harm in leaving the machine booting on the older kernel or should I recompile the 2.6.24-22 kernel and if so how?

Plucked up courage and purged my 2.6.24-19 kernel ... deleted the folder extras created in /lib/modules/2.6.24 by the driver compile ... then reinstalled the kernel and everything is hunky-dory:)

---

