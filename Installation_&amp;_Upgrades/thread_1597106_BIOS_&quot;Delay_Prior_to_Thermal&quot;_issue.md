---
title: "BIOS &quot;Delay Prior to Thermal&quot; issue"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by ryecomp on 2010-10-14
H/W : Intel 1.6GHz, BioStar U8548
S/W : Ubuntu 8.04 + RTAI + EMC2 (CNC controller)

In configuring CNC controller system, latency-test must be run
to find maximum jitter of the system. It counts about 17,000 ns
for few minutes, then it suddenly rise to 260,000 ns. It is impossible
to control CNC with such large jitter.

In tracing this problem, I found that Award BIOS setting
"Delay Prior to Thermal" is firmly engaged in making a problem.
When I set this setting to 4 minutes, it makes large jitter periodically
with exact 4min 15sec period. When I changed this setting to 8 minutes,
its jitter is 8min 15sec period.

But, there is no option to disable this BIOS setting.

I heard that ACPI enabled OS can take over the ACPI function of the
BIOS (which may include this "thermal" setting), but RTAI tuned
kernel don't include ACPI modules.

Is there any solution to this problem ? If I recompile kernel with
RTAI with ACPI processor module enabled, would it be a another
problem maker ?

---

### Post by grey1beard on 2010-10-19
Hi ryecomp.
Is it possible to avoid this as an issue if in fact you have an overheating problem in your processor?
I realise it's not the point you were asking, but would this be another way of dealing with the cause of the problem, rather than the symptom - the activation of the thermal control inside your chip, leading to the increased jitter.
When I was first trying out emc2, before discovering that using a laptop was not a good idea, I was horrified to discover the carpet of hair, crud and dust that had completely blocked the cooling fins inside my toshiba, and what a difference it made to performance generally to peel it off.  :D
Hope this might help,
John

---

