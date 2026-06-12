---
title: "Macbook pro - Lucid - Audio Issues"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by swpx5LFj on 2010-03-03
Hi all, 

I have recently installed Ubuntu Lucid into my MacBook Pro and I have two things to submit to your attention:

Ubuntu Lucid
> Linux localhost 2.6.32-15-generic #22-Ubuntu SMP Tue Mar 2 02:23:29 UTC 2010 x86_64 GNU/Linux


MBP HW Version:
> MacBookPro2,2


1) Audio issue
> cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9221 A1
I heard a continuous whistle/hiss except when some "audio event" occur but after a while that noise come back

2) I have installed into my notebook an SSD that "make noise" every time it writes some data. 

HW Type:
> sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       TEAM_Combo_SSD

I suppose these problems are related  

Any ideas?
I guess someone can help

Cheers :)

---

