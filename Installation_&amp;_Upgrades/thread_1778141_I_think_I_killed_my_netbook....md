---
title: "I think I killed my netbook..."
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by Bakerbakura on 2011-06-08
Hi

Today I was upgrading my netbook with Ubuntu 10.10 on it to 11.04 via the Update Manager. I got a few errors and the Update Manager seemed like it wasn't continuing, so decided to exit it. It didn't respond so after a while I decided to restart the netbook. However the on/off/standby/restart, etc. button in the top right wasn't responding either, so I decided to force a shutdown with the power button on my netbook. Now Ubuntu doesn't start up, and gives me an error along the lines of:

Kernel panic - not syncing: Attempted to kill init!
Pid: 1, comm: init Not tainted 2.6.35-28-generic #50-Ubuntu

Now could I in some way repair my Ubuntu installation while still keeping the files I already have on my computer? Maybe via booting from a flash drive or something...?

Thanks!

---

### Post by garvinrick4 on 2011-06-08
Do you have the flashdrive you installed Ubuntu with?

---

### Post by Bakerbakura on 2011-06-13
I don't have the flash drive I installed Ubuntu originally with anymore - I upgraded to a larger one a few weeks ago. Would it help if I just made another install-Ubuntu-from-flash flash out of the one I have now?

---

### Post by pricetech on 2011-06-13
Boot to a live session, presumably USB in your case, and mount the hard drive if it doesn't auto mount.

Copy your data to safe place, then you can begin to fix your computer.

After this, make sure your backups stay current and never attempt an upgrade without a current backup.

Good luck with it.

---

