---
title: "Primary to extended"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by leo999 on 2007-04-28
Hi
I just installed Fiesty for the first time and it went well without a hitch. However when I logged back into XP I couldnt partition the rest of the unallocated space as I already have four primary partitions. Is there any way I could change the swap and root partitions from primary to extended without reinstalling the OS? Thanks for your help.

---

### Post by louieb on 2007-04-28
Yes but reinstalling is by far easier.
Short of it.
[LIST]
[*]Create logical partitions
[*]copy current install partitions to new
[*]modify /etc/fstab
[*]modify /menu/boot/grub
[*]reinstall grub[/LIST]

---

### Post by leo999 on 2007-04-29
Thanks. I would reinstall. I am not a pro to be able to do all that.

---

