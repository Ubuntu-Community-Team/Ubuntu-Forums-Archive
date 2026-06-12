---
title: "PCIE Bus Error while booting 10.05 64"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by ssottile70 on 2010-07-19
Pointer to BIT loadval table invalid (nouveu drivers)
Hello,

I get this odd behavior when I boot by 10.04 Kubuntu version on a EliteBook 8540w laptop. 

============
[FONT="Courier New"]Jul 19 10:43:00 ssottile-laptop kernel: [   21.072865] pcieport 0000:00:03.0: PCIE Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, id=0018(Requester ID)
Jul 19 10:43:00 ssottile-laptop kernel: [   21.072889] pcieport 0000:00:03.0:   device [8086:d138] error status/mask=00004000/00000000
Jul 19 10:43:00 ssottile-laptop kernel: [   21.072939] pcieport 0000:00:03.0:    [14] Completion Timeout     (First)
Jul 19 10:43:00 ssottile-laptop kernel: [   21.072954] pcieport 0000:00:03.0: broadcast error_detected message
Jul 19 10:43:00 ssottile-laptop kernel: [   21.072959] pcieport 0000:00:03.0: broadcast mmio_enabled message
Jul 19 10:43:00 ssottile-laptop kernel: [   21.072963] pcieport 0000:00:03.0: broadcast resume message
Jul 19 10:43:00 ssottile-laptop kernel: [   21.072968] pcieport 0000:00:03.0: AER driver successfully recovered
Jul 19 10:43:00 ssottile-laptop kernel: [   21.072972] pcieport 0000:00:03.0: AER: Multiple Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073010] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073014] pcieport 0000:00:03.0: AER: Multiple Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073050] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073054] pcieport 0000:00:03.0: AER: Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073090] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073094] pcieport 0000:00:03.0: AER: Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073191] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073195] pcieport 0000:00:03.0: AER: Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073231] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073235] pcieport 0000:00:03.0: AER: Multiple Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073272] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073276] pcieport 0000:00:03.0: AER: Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073312] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073316] pcieport 0000:00:03.0: AER: Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073352] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073356] pcieport 0000:00:03.0: AER: Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073392] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073396] pcieport 0000:00:03.0: AER: Multiple Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073436] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073470] pcieport 0000:00:03.0: AER: Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073516] pcieport 0000:00:03.0: can't find device of ID0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073519] pcieport 0000:00:03.0: AER: Uncorrected (Non-Fatal) error received: id=0018
Jul 19 10:43:00 ssottile-laptop kernel: [   21.073556] pcieport 0000:00:03.0: can't find device of ID0018[/FONT]
============

Kernel used is 2.6.32-23-generic #37-Ubuntu SMP.

Thanks
/ss

---

