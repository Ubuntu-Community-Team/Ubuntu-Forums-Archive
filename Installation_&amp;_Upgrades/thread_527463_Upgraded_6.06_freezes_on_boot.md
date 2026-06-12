---
title: "Upgraded 6.06 freezes on boot"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by mucker on 2007-08-16
Hi folks,

I need help. I've recently installed Ubuntu 6.06 LTS on an IBM Thinkpad T20 from a bona-fide distribution disk with no problems at all.

As the disk was not recent, I was prompted to install 255 updates, which I happily did. It took a while, but  they installed ok. Now when I boot my laptop, it hangs on Saving Vesa State.

I've searched high and low for a solution, and tried a few things:

- set the Save_VBE_State = false in the etc/default/acpi-support file.
- added the acpi-off and noacpi to the kernel boot options.

None of these work.

However, when the freeze occurs, I can usually unfreeze it by switching between hibernate, VGA-off & switch VGA output (Fn+F3, Fn+%4, Fn+F7). This works most of the time, but it's a right pain when I have to do it everytime.

Anyone got any ideas on this?

To confirm, I'm running an IBM T20 with 384Mb Ram, 6Gb HDD, and D-link DWL-G650 wireless card.

Apart from that, I think Ubuntu is the dogs danglies!

Many thanks,

//mucker

---

### Post by mucker on 2007-08-18
*bump* anyone?

---

