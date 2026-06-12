---
title: "2x 2TB mirrored via software, at install or post-install?"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by RHAnthony on 2011-10-25
I'm looking for some guidance here because I have not done anything like this before during an install.

I have a machine that I am going to put Ubuntu Server (amdx64) on.  I would like to use software (MD, LVM, etc) to make the 2 SATA 2TB drives mirrors of each other (RAID 1).

The machine is an HP and offers a hardware RAID controller, but I am reading all of the place that a software solution would be much better, as I can more readily access my data should something go wrong in the future that way.

What I really need to know though, is what should I be using here?  Mainly I'm looking at an ease of use/install kind of goal, as this machine really isn't going to change at all in the foreseeable future.  I don't even specifically need a performance boost from the setup, as much as I'm looking for mirrored content so I can survive a single disk failure scenario.

The machine will be hosting virtual machines via KVM, if that matter at all.

So gurus... What do I want to use?  LVM or MD?  Should I do this at time of install, or post-install?  I've worked with either so again, ease of use/install is my priority this go-round.

---

