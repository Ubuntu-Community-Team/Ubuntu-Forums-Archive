---
title: "Latest update of 16.04 broke boot: Can't read CTR while initializing i8042"
date: 2018-02-14
forum: Installation &amp; Upgrades
---

### Post by samig59 on 2018-02-14
Hi!

After the latest update of 16.04 my system became essentially useless. 
It throws "**Can't read CTR while initializing i8042"** and drops into single-user mode.
Stangely, the keyboard is functioning.

Any suggestion of how to bypass this and get back a fully functioning system?

Thank you,

/S.

---

### Post by cruzer001 on 2018-02-14
Hello

Googling the error lead me to this HP link.

[https://support.hpe.com/hpsc/doc/public/display?docId=emr_na-c05065583&sp4ts.oid=7271259](https://support.hpe.com/hpsc/doc/public/display?docId=emr_na-c05065583&sp4ts.oid=7271259)

I would suggest dropping back to previous kernel at boot (grub>advance options) and see if its kernel related.

---

### Post by samig59 on 2018-02-15
Thank you. Indeed, I have seen that message before. However, to "safely ignore it" doesn't lead anywhere. Yes, I suspect that it is a kernel issue. I will follow your suggestion and try to boot into the previous kernel (actually the same thing has happened before after updating another Linux distro - I resolved the problem then by re-installing the old version). But it is really shame that an update can break the system like that.

Best regrads and thank you

---

### Post by samig59 on 2018-02-15
The old Kernel 4.[FONT=monospace][COLOR=#000000]10.0-28-generic has no problem at all. Strange that the newer kernel is broken![/COLOR]
[/FONT]

---

### Post by cruzer001 on 2018-02-15
16.04 also uses and supports the 4.4 kernel for the life of the install (5 years).  You are currently on the HWE version that upgrades the kernel every 6 months.  I would try this kernel and if it works, remove the HWE stack.

The 4.10 kernel series is nearly at end of life.  All HWE kernels are only supported for 9 months.  Only the 4.4 kernel has long term support (LTS).

---

