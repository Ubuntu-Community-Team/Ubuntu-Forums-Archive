---
title: "Upgraded Edgy to Feisty does not boot kernel"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by DKnight on 2007-04-19
Hi.
I just upgraded my Edgy installation to Feisty, and I'm having a (critical) problem.
When I try to boot up the new kernel 2.6.20-15, it shows the ubuntu logo with the progress bar (a slim line of it completed), but the comp does nothing. It just hangs there (I've waited quite a long time) with no activity.
Trying to boot the same image in recovery mode shows that the startup process stops at **"Waiting for root filesystem"**. There is no signal of activiy from the HDD btw.
The old 2.6.17-10 kernel boots just fine, but I dont know if I should use that in Feisty, and there's clearly something wrong with the upgrade.

Any help is appreciated, thanks.

---

### Post by Mongoose on 2007-04-19
This is a common issue when feisty was in beta.  Install the next to the last -14 kernel package or bulid a new kernel yourself. I had some of the -15 kernels working, but they broke health sensors and were generally unstable.  It mostly affects sata users.

---

### Post by DKnight on 2007-04-20
Thanks for the reply, but I finally solved it by replacing:

```
UUID=eadf8f2b-b50c-4681-bce4-28ac9aafb9cb      /               ext3    defaults,errors=remount-ro 0       1

UUID=9b4d7e64-0cb2-46c1-b84d-2e56a30f3f90    /home           ext3    defaults        0       2

UUID=837830f2-6caa-4ac0-98e3-7307ef1f7da1     none            swap    sw              0       0
```

with

```
/dev/sda2				 /               ext3    defaults,errors=remount-ro 0       1

/dev/sda4				 /home           ext3    defaults        0       2

/dev/sda5				 none            swap    sw              0       0
```

in my fstab file.

Now it boots flawlessly!\\:D/

---

### Post by zenwalker on 2007-04-20
Oh ya, its not the problem with Fiesty. Its the latest new convention used by Kernel. The 2.6.20.x ver of kernel has changed the convention of calling the PATA disks as SDA instead of good old HDA. I wonder why the kernel team did that?

Any ways i came to new this stuff when the kernel was released quite a long back lol. Just i didnt rem which reading your thread. And now i rem whats wrong.

Btw, i hope your enjoying with the mighty beast (fiesty) ;)

---

