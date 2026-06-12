---
title: "Can't install Ubuntu on UEFI laptop"
date: 2017-11-21
forum: Installation &amp; Upgrades
---

### Post by stephenarathbone on 2017-11-21
Hi,

I brought an Iota laptop off Amazon and want to put Ubuntu on it.

I've created a Ubuntu 17.10 USB using etcher.io which works on my other laptop but not this new one.

Secure boot is disabled but when I try to boot from the USB I get only an prompt underscore in the top left.

I've also tried launching the efi shell from the bios and mounting and manually running the bootx86.efi but get the same result, manually running the windows bootx86.efi via efi shell works fine.

Any ideas?

---

### Post by yancek on 2017-11-21
I would suggest you start by reading the link below which is the ofiicial Ubuntu documentation on UEFI booting/dual booting.  Do you have a windows install?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-11-21
What brand/model laptop?
What video chip?

Some very lightweight systems use 32 bit UEFI even though 64 bit systems.
That was back when Linux did not have a 32 bit UEFI boot loader, so they tried making it Windows only.

---

