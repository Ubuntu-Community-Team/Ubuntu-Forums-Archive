---
title: "Grub rescue, OS not starting"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by matanc1 on 2013-01-19
I've dual booted both windows 8 and ubuntu on my laptop.
For some reason the WIFI stopped working one day so today I decided to format the laptop and reinstall it to check if that'll fix my WIFI problem (when I say stopped working I mean that it always showed that the hardware switch is disabled even when it wasn't). 

I've used my laptop's rescue media to reinstall the factory windows 7 and now I get the grub rescue screen. 
I don't know what to do! I can't load windows. 
How can I fix this?

---

### Post by Laiquendi on 2013-01-19
Have you changed partitions during installation? Windows is "rescuing itself" from partition, which may be deleted/moved during other OS installation.

---

### Post by matanc1 on 2013-01-19
> **Laiquendi said:**
> Have you changed partitions during installation? Windows is "rescuing itself" from partition, which may be deleted/moved during other OS installation.

What I meant by rescue partition is that the Windows 7 installation  is a partition by itself ( there is no windows 7 disc ).
I can usually install by clicking f9 on boot but it doesn't work now as well.

---

### Post by darkod on 2013-01-19
Looks like windows didn't install it's bootloader. Or the computer was switched from uefi boot to legacy boot. If it came in uefi boot I think the factory restore would work only if used with uefi boot. In that case you are not using grub2 to boot, you are using the uefi boot manager/loader.

Besides, this is a windows issue. You might get better help on the windows forums. The factory restore should return the computer to factory state, how it was delivered. Why your factory restore doesn't do that, is mostly a windows question.

You can easily delete grub2 from the MBR, but that's not the point. The point is what kind of bootloder you need to have there so that your computer can boot. The restore process should have done that job for you.

---

