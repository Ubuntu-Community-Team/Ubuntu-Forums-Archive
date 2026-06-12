---
title: "upgrade 18.04 &gt; 19.04 worked fine except kernel stuck on 4.18.25"
date: 2019-07-16
forum: Installation &amp; Upgrades
---

### Post by rbmorse on 2019-07-16
I thought I'd exercise my vast knowledge of Ubuntu and bypass the requirement to upgrade to 18.10 as an intermediate step when migrating from 18.04 to 19.04.  Karma's a harsh mistress. 

Actually, everything worked well.  Purged the nvidia driver (reboot to nouveau), changed the repo sources and did the dist-upgrade.  After a reboot the system came up as expected with no obvious problems. 

 About reports 19.04/Gnome 3.32, but uname still shows I'm on the 4.18.25 kernel. 

I could live like this, I suppose.  I could do a fresh, bare metal install from the 19.04 .iso but I'm not certain if the systemd fix that allows Disco to run on AMD Ryzen 3000 cpus has made it to the installation .iso (nothing is release notes, yet). Or, I could just restore the partition image of 18.04 I made before this adventure began and wait until 19.10 gets released. 

But, what I'd really like to do is install a 5.x series kernel into what I have now.  Can I just select the 5.0.20-x generic image in repo with Synaptic and go from there? 


TIA. You guys are great.

---

### Post by deadflowr on 2019-07-16
issue is that Ubuntu 18.04 with the 4.18 kernel is from the linux-hwe packages.
There is no such thing as hwe on 19.04 systems. (hwe is for lts)
You need to install the linux-generic packages in order to get the 19.04 correct kernel.

---

### Post by CatKiller on 2019-07-16
I'd imagine that at some point you've removed the linux-generic metapackage, so your kernel couldn't get updated with the upgrade. That's probably the easiest way to get up to date.

---

### Post by rbmorse on 2019-07-16
My limited knowledge brings the power to create great havoc.  

Yes, of course.  HWE.  I knew that.  sigh.   

Thank you.

---

### Post by deadflowr on 2019-07-16
> **CatKiller said:**
> I'd imagine that at some point you've removed the linux-generic metapackage, so your kernel couldn't get updated with the upgrade. That's probably the easiest way to get up to date.

If installed from the 18.04.2 point release installer then the linux-image/headers/generic package(s) never existed.
That comes with the hwe based packages.

In a twist, Ubuntu 18.04.3 should be arriving sometime soon (later this month or early next month)
Which will actually come with the 19.04 kernels.

Add that with the fact that 18.10 is coming to it's EOL, they should be getting ready to allow upgrades from 18.04 to 19.04 directly.
(If they follow the trend they've been using for the last two LTS cycles)

I think though that when that happens you'd already have the upgraded 19.04 kernel on 18.04, so there wouldn't really be an issue with it.

---

