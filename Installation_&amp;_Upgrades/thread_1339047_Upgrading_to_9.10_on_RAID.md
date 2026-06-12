---
title: "Upgrading to 9.10 on RAID"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by ggb-uk on 2009-11-27
I am running a system a pair of RAID-1 disks (NVidia controller).

I recall when 9.04 first came out, and I casually clicked on the upgrade button, and was left with a useless machine until I managed to go in and add the RAID drivers to the boot disk image (IIRC, only after degrading the RAID and then rebuilding it).

I now see that an upgrade to 9.10 is available, but am reluctant to just click on the button to run the upgrade unless I am sure that I will not have to spend the next couple of days fixing the same problem (especially as I do not have as much time as I had then to do system repairs).

Can anybody give credible assurances that upgrading on a RAID-1 system now works without repairs needing to be made, or in what way I might pre-empt the need to repair the system after the upgrade without having to put up with a non-working system after the upgrade?

Note that I am running AMD 64 bit Ubuntu, if that makes any difference to anybody.

---

### Post by lemming465 on 2009-11-28
9.10 has much more aggressive firmware RAID support.  Try a live 9.10 CD; if it sees the disk layout the way you want, I would expect an upgrade to proceed OK.  Actually, the biggest RAID problem with 9.10 I've been helping with is dmraid finding remnants of legacy RAID stuff no longer in use.

---

### Post by ggb-uk on 2009-12-26
> **lemming465 said:**
> 9.10 has much more aggressive firmware RAID support.  Try a live 9.10 CD; if it sees the disk layout the way you want, I would expect an upgrade to proceed OK.  Actually, the biggest RAID problem with 9.10 I've been helping with is dmraid finding remnants of legacy RAID stuff no longer in use.

Thanks for the reply.

Sorry it took a while to get back, I needed a little free time to give this a go (and back things up, just in case it did not work).

Just to let you know I tried the live CD, it worked, so then went ahead with the upgrade, and it all went smoothly (as far as I can tell so far).

Thanks again.

George.

---

