---
title: "easiest way to revert/upgrade to a specific kernel version?"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by bravegag on 2012-06-29
Hello,

What is the easiest way to revert back to an older kernel version? 

If I do a fresh install, what's the easiest path to update to a specific kernel version?

I have two machines and need both to be in perfect sync version both are 11.10 based. In one I have kernel version 3.0.0-21-generic which broke the C++ project I am working on and would like to revert it back to 3.0.0-19-generic.

Likewise I had to fresh reinstall 11.10 on my Desktop due to unusable/non-bootable system after upgrading to kernel 3.0.0-22-generic. The fresh install from CD installs version 3.0.0-12-generic and I would like to upgrade it specifically to version 3.0.0-19-generic. 

How can I do this? 

Many TIA,
Best regards,
Giovanni

---

### Post by black veils on 2012-06-29
i think you can just enter Grub during boot, and select the previous kernel (check the number difference). if you dont see Grub, restart and hold the **Shift** key during boot.

---

### Post by bravegag on 2012-06-29
> **black veils said:**
> i think you can just enter Grub during boot, and select the previous kernel (check the number difference). if you dont see Grub, restart and hold the **Shift** key during boot.

thank you.

---

