---
title: "Partitions disappeared"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by raymond350 on 2007-11-12
I tried installing Ubuntu on my Vista machine, and I shrink the volume on my D:, creating 10GB of space, instead of C: (where Windows is installed).

However, the installation stopped at 82% and I restarted my system when I could not access Windows again (No OS found msg appeared). 

I booted up using the Ubuntu CD, chose manual partition, and deleted and created a logical drive for that 10GB space. An error msg appeared and couldn't continue so I restarted my system again.

Upon restarting, realised all my partitions are gone, but all my files in my C: and D: were still intact. How should I proceed to install Ubuntu from now on? and is there a way to enter Windows again?

Appreciate any help on this matter. Thanks

---

### Post by confused57 on 2007-11-13
If you have a Vista install DVD(not a recovery disk), you could try repairing Vista:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

---

### Post by raymond350 on 2007-11-13
My laptop doesn't come with Windows Vista CD. There is a one button recovery option though, but I would use it as a last resort as it restore everything back to factory settings.

---

### Post by bulldog on 2007-11-13
Can you boot the live cd and post the output of```
sudo fdisk -l
``` please.

---

