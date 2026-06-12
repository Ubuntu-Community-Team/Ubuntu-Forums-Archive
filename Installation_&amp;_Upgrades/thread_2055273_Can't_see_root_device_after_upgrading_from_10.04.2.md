---
title: "Can't see root device after upgrading from 10.04.2 to 10.04.4"
date: 2012-09-09
forum: Installation &amp; Upgrades
---

### Post by jJackFlash on 2012-09-09
Hi,

In preparation for upgrading to 12.4 I upgraded from 10.04.2 to 10.04.4. I only got an error message about hdparm at the end of the process.

After restart, the system doesn't boot.

First it complains about /scripts/init-premount/mdadm and /scripts/init-premount/lvm2 (add_mountroot_fail_hook) and then "Gave up waiting for root device..." and a scaring "ALERT! /dev/mapper/uServer-root does not exist. Dropping to a shell!".

I first though it was a hard drive hw problem but I burned an alternate CD and after booting from it I was able to use a shell on /dev/mapper/uServer-root and browse it.

I've tried to use Grub to boot from the previous kernel but the same error came up again.

Any hint on how to get my system back to life will be appreciated.

j

---

