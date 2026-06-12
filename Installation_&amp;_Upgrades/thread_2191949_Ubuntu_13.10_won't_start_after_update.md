---
title: "Ubuntu 13.10 won't start after update"
date: 2013-12-05
forum: Installation &amp; Upgrades
---

### Post by hSync on 2013-12-05
Hi,


Yesterday i updated my Ubuntu 13.10 with the new updates (~60mb) then i rebooted.


After that, the system won't start, i get a black screen and my cursor is a X.


I think the update name is 3.11.0-14 generic.


Now i need to go recover mode and select 3.11.0-13 generic to use ubuntu.


I use nvidia driver 331.20 64bit.


Is there any way to fix this?


Thank you!

---

### Post by oldfred on 2013-12-05
How did you install nVidia driver?

If you install from Ubuntu repository it is integrated into the new kernel automatically, but if you directly downloaded from nVidia, you in effect have to reinstall with every kernel update.

So can you boot new kernel with nomodeset? Then reinstall nvidia?

---

### Post by hSync on 2013-12-05
> **oldfred said:**
> How did you install nVidia driver?

If you install from Ubuntu repository it is integrated into the new kernel automatically, but if you directly downloaded from nVidia, you in effect have to reinstall with every kernel update.

So can you boot new kernel with nomodeset? Then reinstall nvidia?

Yes, i downloaded from nvidia.
Thank you, i resintalled the driver and now is working! Thank you very much!

---

### Post by oldfred on 2013-12-05
Glad that worked. 
You can change to solved. See my signature for info if not sure how.

---

