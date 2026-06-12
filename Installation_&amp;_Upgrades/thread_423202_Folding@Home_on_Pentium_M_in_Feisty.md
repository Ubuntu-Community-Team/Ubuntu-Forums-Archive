---
title: "Folding@Home on Pentium M in Feisty"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by QuantumCaffeine on 2007-04-25
Hi all,

I've just upgraded to Feisty from Dapper (never quite got around to installing Edgy), and I can't get the Folding@Home console client to play well with Speedstep. 

My processor is a 2GHz Pentium M which, thanks to powernowd, drops to 800MHz when idling. In Dapper, the Folding@Home client respected that, but in Feisty it pushes the processor to run at 2GHz all the time. It runs with niceness 19, so I don't understand why this is happening. Is it a problem with the client, or something to do with powernowd?

Any help would be much appreciated; if I can't solve the problem I'll probably have to stop contributing to Folding@Home, which would be a shame.

Regards,

QC

---

### Post by laredo7mm on 2007-05-07
> **QuantumCaffeine said:**
> Hi all,

I've just upgraded to Feisty from Dapper (never quite got around to installing Edgy), and I can't get the Folding@Home console client to play well with Speedstep. 

My processor is a 2GHz Pentium M which, thanks to powernowd, drops to 800MHz when idling. In Dapper, the Folding@Home client respected that, but in Feisty it pushes the processor to run at 2GHz all the time. It runs with niceness 19, so I don't understand why this is happening. Is it a problem with the client, or something to do with powernowd?

Any help would be much appreciated; if I can't solve the problem I'll probably have to stop contributing to Folding@Home, which would be a shame.

Regards,

QC

Folding at home should max out your cpu.  Just because it is set at a nice of 19 doesn't mean it won't use your cpu 100%, it just means every other app will have priority over FAH.  When your cpu goes to idle, FAH takes it to 100% utilization.

If you are folding, why don't you want it to run at 2GHz?

---

