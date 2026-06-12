---
title: "swap partition would be deleted safely with 4M ram?"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by xiaoyong on 2011-04-23
RAM of the machine is 4M.  I never see the swap partition has been used via system monitor.  So can I safely delete the swap partition?

---

### Post by mörgæs on 2011-04-23
I  guess you mean that you have 4 G of ram.

Why do you want to delete the swap partition? Are you really low on hard disk space?

---

### Post by dino99 on 2011-04-23
> **xiaoyong said:**
> RAM of the machine is 4M.  I never see the swap partition has been used via system monitor.  So can I safely delete the swap partition?

bad idea (you need it for suspend/hibernation, and with heavy work)

---

### Post by walt.smith1960 on 2011-04-23
> **dino99 said:**
> bad idea (you need it for suspend/hibernation, and with heavy work)

A swap partition is not required for suspend.  It _is_ required for hibernation.  I've not used 1 Gb. of RAM let alone 4 but I don't do things like video editing or run virtual machines so I'm not a heavy user.  On machines with limited DRAM, I've created a swap file.  That seems to do everything required except support hibernation and doesn't take up 1 of the 4 allowed partitions.  Swap file performance was pretty poor on earlier Linux kernels but modern kernels seem to be on a par with swap partitions. Just another option.

---

### Post by varunendra on 2011-04-24
> **xiaoyong said:**
> RAM of the machine is 4M.  I never see the swap partition has been used via system monitor.  So can I safely delete the swap partition?

Yes you "can", but you shouldn't.

I also guess you meant 4 'GB' RAM, and like mörgæs hinted, unless you desperately need that disk space the swap has taken up, you should keep it.

Or, if you are absolutely sure you are never going to use up more than 3.5 (approx. vol.) GB of memory, then you can safely do away with swap. This means no hibernation, nothing like heavy video editing, CAD or animation apps, or simultaneous running of too many apps (you may test yourself all the 'extremities' possible in your case).

---

### Post by xiaoyong on 2011-04-24
Sorry for the typo, not 4M, but 4G.  I decide to keep the swap partition which has been decreased from 8G to 4G.  Thanks for the discussion here.

---

### Post by mörgæs on 2011-04-24
Good, please mark the thread 'solved'.

---

### Post by wojox on 2011-04-24
> **walt.smith1960 said:**
> A swap partition is not required for suspend.  It _is_ required for hibernation.  I've not used 1 Gb. of RAM let alone 4 but I don't do things like video editing or run virtual machines so I'm not a heavy user.  On machines with limited DRAM, I've created a swap file.  That seems to do everything required except support hibernation and doesn't take up 1 of the 4 allowed partitions.  Swap file performance was pretty poor on earlier Linux kernels but modern kernels seem to be on a par with swap partitions. Just another option.

Hibernation = suspend to disk.

---

