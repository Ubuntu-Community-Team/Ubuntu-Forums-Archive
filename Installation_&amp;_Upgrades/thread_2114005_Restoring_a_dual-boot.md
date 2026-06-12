---
title: "Restoring a dual-boot"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by jimw on 2013-02-08
I previously had a dual-boot system on my computer, but in installing the latest Ubuntu (12.10) I managed to lose the dual boot.

All the Windows partition is still there, and all the files accessible.  Is there some way I can restore the dual boot?

JimW

---

### Post by papibe on 2013-02-08
Hi jimw.

You can use the same Ubuntu installation media as a Live CD/USB, and repair most boot issues. Take a look at this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") for details.

Let us know how it goes.
Regards.

---

### Post by darkod on 2013-02-09
If you had windows in uefi boot but installed ubuntu in legacy mode that will not create a correct dual boot. These days it's the most common case of dual boot not working. Both OSs seem to be in the same mode but since uefi is rather new people are still not aware of it.

If you install boot-repair in ubuntu, it can help in many cases. Or you can use it first without doing the Recommended repair, only to make the Bootinfo and post the link of the results so we can see more details.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

In case you do have windows in uefi, some basic info about installing ubuntu in uefi mode:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I have seen it mentioned that boot-repair can convert youe legacy ubuntu to uefi ubuntu if you need to do that, but I have never done that operation myself. Never needed to, I don't use uefi.

---

