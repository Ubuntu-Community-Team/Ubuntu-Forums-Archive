---
title: "Anybody able to get rtl8187L wireless chipset working?"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sunkssss on 2008-10-27
Hello all,

Has anybody had any luck getting the rtl8187L chipset working in 8.10 amd64? I installed 8.10 and the wireless works initially as it does in 8.01 but suffers from a similar issue, it drops to zero throughput after a while. 

How about getting ndiswrapper to work? I installed ndiswrapper, but when I went to install the windows drivers and reboot, the system will not load after login. It just shows an orange screen and the white pointer. 

Perhaps I did not install ndiswrapper correctly, is there a walk through for this process yet?

---

### Post by aethralis on 2008-10-27
Maybe the comments for this bug report offer some help (if you already have not looked at this, of course):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473)

---

### Post by sunkssss on 2008-10-27
Unfortunately I think I'm too much of a noob to get any further than the folks in that thread who seemed to really know what they were talking about. I read somewhere that Gutsy Gibbon worked but somewhere in the transition to 8.01 something went wrong. I've spent three days and nights trying to figure it out to no avail, so I'm just going to Gutsy and wait a while until folks find a solution. Thanks for the help.

---

### Post by sunkssss on 2008-10-28
Just in case anybody else has this issue or was wondering, using WICD I was able to connect stably to an unsecured wireless network. While this isn't ideal, it is certainly better than no network at all.

---

