---
title: "Persistent USB Installation Longevity?"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by Zorael on 2007-10-13
I found some guides on how to install Ubuntu on an USB stick here on the forums, but I'm a bit hesitant.

I read over at the [Wikipedia entry](http://en.wikipedia.org/wiki/Usb_stick#Weaknesses) that flash memory eventually fail after a certain number of write operations.

[quote="Said article"]Like all flash memory devices, flash drives can sustain only a limited number of write and erase cycles before failure. Mid-range flash drives under normal conditions will support several hundred thousand cycles, although write operations will gradually slow as the device ages. This should be a consideration when using a flash drive to run application software or an operating system. To address this, as well as space limitations, some developers have produced special versions of operating systems (such as Linux) or commonplace applications (such as Mozilla Firefox) designed to run from flash drives. These are typically optimized for size and configured to place temporary or intermediate files in the computer's main RAM rather than store them temporarily on the flash drive.[/quote]

I'd like mine to be persistent and save changes; kind of like something between a Live CD (if I can find a way to include the installer), a backup OS if my partition table is lost, and a way to show off Ubuntu to others still stuck with Windows.

But I know that there's a lot of random HD activity with any OS; swapping, caching, saving settings, etc. But this should all be in my home directory, /tmp, and /var, **right?** Or is there root permission write activity performed at boot?

Is there some widespead but to me unbeknownst way to make at least the home dir into an iso image, mounted upon boot and changes saved upon shutdown? Also make it not swap at all, ever, keeping swap, /tmp and /var in a ramdisk?

It'd lose changes if the system crashed, but I can live with that. And I guess the system would need more RAM to boot than otherwise.


But is it possible, or is there no choice but to let the USB stick slowly expire?

---

### Post by Zorael on 2007-10-15
Bumpity bump.

---

