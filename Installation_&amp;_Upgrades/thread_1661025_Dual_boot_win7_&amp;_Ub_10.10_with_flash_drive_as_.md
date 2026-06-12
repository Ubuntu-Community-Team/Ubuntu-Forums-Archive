---
title: "Dual boot win7 &amp; Ub 10.10 with flash drive as &quot;key&quot;?"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by Circlotron on 2011-01-06
I have a new machine with windows 7 already on it and I want to to Ubuntu 10.10 on as well, on it's own separate physical HDD. Moreover, I want to have it set up so that if other family members switch the thing on it will boot to win7, but if I come along and put my USB flash drive in the socket then boot it will go straight to Linux on the Linux HDD. 

I ABSOLUTELY want to avoid using a boot manager on the windows HDD. Just have the USB flash (if present) point to the Linux HDD.


There are plenty of how-to's for booting and running entirely from USB, or using boot managers on one or the other hard drive but I want to keep both hard drives untouched.

Can anyone please point me to a how-to for this method somewhere?

---

### Post by sanderd17 on 2011-01-06
It should be possible if you do the following. I assume you have already win 7.

install ubuntu the normal way, which would lead to a grub screen if you start it.

repair the windows bootloader, this should not damage the real ubuntu installation.

install ubuntu to an USB stick (not a live USB!), that installation should install grub in the USB and discover the two other systems.

When you boot without USB, windows will start. When you boot with USB and you select to "boot from USB", GRUB will be shown in which you can choose ubuntu from your HDD (you can make this the default choice.

I say this would be possible, but I have no experience with it. I can imagine that you will have to redo the proces a few times until it works.

---

### Post by Mark Phelps on 2011-01-06
> **Circlotron said:**
> ... but I want to keep both hard drives untouched.

In terms of the suggestion of installing with both drives connected, apparently then overwriting the MBR on the MS Windows drive, and then having to repair that MBR later -- seems like a lot of extra, unneeded work.

The simpler approach (and, this is what I do as well) is to have only the Ubuntu drive connected when you install Ubuntu.  That way, there is NO risk of messing up the MBR on the MS Windows drive.  AND ... there is nothing you have to go back and repair.

---

### Post by sanderd17 on 2011-01-06
> **Mark Phelps said:**
> In terms of the suggestion of installing with both drives connected, apparently then overwriting the MBR on the MS Windows drive, and then having to repair that MBR later -- seems like a lot of extra, unneeded work.

The simpler approach (and, this is what I do as well) is to have only the Ubuntu drive connected when you install Ubuntu.  That way, there is NO risk of messing up the MBR on the MS Windows drive.  AND ... there is nothing you have to go back and repair.

I overlooked the fact that he had 2 drives. You are right: unconnect the windows drive and install ubuntu on the second hdd and on the USB.

---

