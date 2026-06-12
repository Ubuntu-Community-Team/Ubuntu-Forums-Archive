---
title: "Ubuntu boot woes"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by DougZ on 2005-04-19
I've just tried a couple times to install Hoary onto my Toshiba Tecra S1.  I'm dual-booting with XP on the first partition.

The first time it installed no problem.  I shut it down and restarted it a few times with no problems.  I even had the XP bootloader launch Ubuntu, rather than using grub. (Use this laptop at work and it looks normal and  "uninteresting" to shoulder-surfers if the normal XP boot screen comes up  ;-) )

This worked fine the first couple of reboots. Was able to swtich between XP and Ubuntu successfully several times. Suddenly without warning it now gets as far as "grub loading stage 1" then reboots, and so on in an endless loop.

Reinstalled, this time staying with grub as the bootloader.  Worked beautifully the first 2 or 3 boots.  Then suddenly the same problem.  Xp still boots and works fine.

This is just "odd" for want of a better term.

Any suggestions?

---

### Post by speedman on 2005-04-19
Is XP restoring it's default boot loader by chance?  Or, do you have an ant-virus app in Windows that is modifying what it perceives to be an altered boot record?


Regards,

SM

---

### Post by DougZ on 2005-04-19
No, I can switch back and forth several times successfully.


BUT only if I keep rebooting (rather than shutdown).  Once I do a complete shutdown, grub is toast.  From that point if grub is the bootloader, I see loading stage 1.5 flash briefly followed by a reboot.  If XP is the bootloader, I can either boot to XP or select Ubuntu, at which point it reboots.

On the outside chance it was because /boot was on a logical partition, I repartitioned to put boot on a primary, but no luck.

But now that I think about it /boot is way towards the end of the drive:
  hda1 - Windows (15 Gb)
  hda2 - Windows data partion (40 Gb)
  hda3...hdax - Linux partitions

Since XP does not easily relocate, I'm stuck with at least keeping the first partition, but I'll try rearranging so /boot is the 2nd partition (best I can do without reinstalling XP - really NOT a option)

But thats a "tomorrow" job as it's heading toward midnight as I write this.

What's funny is it does work, repeatedly, at least until I do a cold boot.

---

