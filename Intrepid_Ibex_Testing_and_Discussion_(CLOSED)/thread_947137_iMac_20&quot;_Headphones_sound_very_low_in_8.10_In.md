---
title: "iMac 20&quot; Headphones sound very low in 8.10 Intrepid"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lucian_sh on 2008-10-14
It's been a while since this problems is around, without a very specific solution, I have a 20" mid 2007 aluminum iMac and I'm running Ubuntu 8.10 Intrepid beta, just updated from 8.04 and everything works fine but the audio, the headphones volume is very very low, I tried all the tricks around, all the mixers are at max, everything unmuted, and checked with various apps. I currently I have installed alsa-driver 1.0.17 the official Ubuntu package and it seems that the bugfix that appeared like a year a go is not fully implemented here.

I'm also posting the output of some diagnostic tools:

- lspci -vvnn
- cat /proc/asound/version
- cat /proc/asound/card0/codec#0
- amixer

So any ideas in how to fix this bug will be appreciated.

---

### Post by cyberdork33 on 2008-10-14
Please create a bug report for this. Kernel Freeze for Intrepid is just around the corner, and this would be an important fix to get into the kernel for 8.10.

[https://edge.launchpad.net/ubuntu/+filebug](https://edge.launchpad.net/ubuntu/+filebug)

It should be marked against 'linux' and 'mactel-support'

---

### Post by lucian_sh on 2008-10-15
> **cyberdork33 said:**
> Please create a bug report for this. Kernel Freeze for Intrepid is just around the corner, and this would be an important fix to get into the kernel for 8.10.

[https://edge.launchpad.net/ubuntu/+filebug](https://edge.launchpad.net/ubuntu/+filebug)

Ok, thanks I just submited the bug report, here is the link.

[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/283589/](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/283589/)

> It should be marked against 'linux' and 'mactel-support'

By the way I'm quite new in launchpad, and didn't found out exactly how to mark the bug... :) How do I do that?

---

