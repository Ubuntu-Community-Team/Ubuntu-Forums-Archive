---
title: "Can a Ubuntu Server 16.04.6 network install load an OEMDRV image before ethdetect?"
date: 2019-08-23
forum: Installation &amp; Upgrades
---

### Post by robroygregg on 2019-08-23
Ubuntu Fans,

I'm trying to network install (using preseed) Ubuntu Server 16.04.6 AMD64 on a computer with Intel X722 Ethernet controllers.  Yet the i40e driver version in Ubuntu Server 16.04.6 is 1.4.25-k, which isn't new enough to support the X722.

So I've compiled i40e 2.9.21 from Intel's source, and made an OEMDRV image for it.

During a manual installation, the Ubuntu installer automatically loads i40e 2.9.21 from the OEMDRV image, and the Ethernet controllers are detected.

Yet during a networked installation, the installer looks for Ethernet interfaces *before *loading the OEMDRV image.  This makes the installation fail because it can't find any interfaces; here's what I see:

[ATTACH=CONFIG]283861[/ATTACH]

Is there anything I can do to make Ubuntu Server 16.04.6 load an OEMDRV image before it looks for Ethernet interfaces?

I'm hoping to accomplish this by using options appended to the kernel command line.  Options in the preseed file won't work, because the preseed can't be fetched until Ethernet's working.

I would like to avoid making a custom ISO/initrd image.

Thanks so much!

Rob Roy

---

### Post by mörgæs on 2019-08-25
On my vanilla 18.04.3 install, ```
modinfo i40e
``` shows that I have release 2.7.6-k.

Is there a certain reason you are sticking to 16.04 and not 18.04.3?

---

### Post by robroygregg on 2019-08-26
[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075"), thanks so much for replying!

Yeah, I noticed that i40e is new enough for my hardware in 18.04, yet I have to stay with 16.04 for this project.

Have a great day.

Rob Roy

---

