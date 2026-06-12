---
title: "[SOLVED] Resize partition = no boot"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by martin_legion on 2008-08-12
Hello, I need some help here
I resized a mandriva partition (don't remember if /var or /) to install xubuntu on the new free space.
I installed xubuntu and all went fine, except that now I boot mandriva, it loads a lot of stuff but it seems that when it tries to load kde it freezes. I can't switch to console or see the last thing that loaded. The only thing that works is ctrl+alt+del. It unloads everything and reboots normally.
I can boot in single-user mode, but don't know what to do.
In mandriva's fstab, partitions are refered as /dev/hdaX, not UUID. I first thught that if I resize a partition the UUID might change and that could be the reason, but it's not the case.
Can anybody help me?...

Thanks

Martín.

---

### Post by sandysandy on 2008-08-12
can u boot xubuntu

if not, give super grub disk a try.

regards

---

### Post by martin_legion on 2008-08-12
> **sandysandy said:**
> can u boot xubuntu

if not, give super grub disk a try.

regards

Yes, I can boot xubuntu. From xubuntu I mounted the / partition of mandriva to see the fstab config.
I can also boot mandriva in single-user mode. Can I try anything from there?
Thanks for the quick reply!

---

### Post by martin_legion on 2008-10-07
I tried Super Grub Disk and solved the issue.
Thanks.

---

