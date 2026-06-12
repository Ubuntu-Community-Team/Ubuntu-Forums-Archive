---
title: "SSD not detected after format for ubuntu install"
date: 2020-04-15
forum: Installation &amp; Upgrades
---

### Post by carsonmiller on 2020-04-15
I'm sure this is an easy fix, but here's the situation.

1. I launched gparted and believe I deleted all partitions for my 256GB SSD not knowing what the hell I'm doing really. I think it got unmounted.

2. I installed Ubuntu onto a USB, and started the installer on my Lenovo X1 Carbon.

3. My SSD is detected in BIOS, but now on gparted & ubuntu installer my SSD isn't detected.

When I launch the ubuntu installer it shows "COMRESET failed (errno=-16) multiple times, then the installer launches.

I ran diagnostic on the SSD in my BIOS/UEFI and it's passing all tests.

* I've tried it with two different USB sticks, one of which is brand new, and in two different USB ports.

---

### Post by CelticWarrior on 2020-04-15
> I launched gparted and believe I deleted all partitions for my 256GB SSD not knowing what the hell I'm doing really.

Definitely NOT a good start. You should know what you're doing otherwise better NOT do it, at all.


> I think it got unmounted.
Obviously. If there are not partitions, there's nothing to mount.

> My SSD is detected in BIOS, but now on gparted & ubuntu installer my SSD isn't detected.
Now, this is quite unusual. If it was detected before it should be detected now. **Have you changed the SATA mode in UEFI ("BIOS") and/or disabled that drive, even inadvertently?**

---

### Post by oldfred on 2020-04-15
Make sure UEFI has drive set to AHCI, not RAID nor Intel RST. 
Not sure if gparted would have worked without that or not.

And many systems need UEFI update and SSD firmware update. Easier with Windows, but most systems will let you download an update file (not the .exe for Windows) into a FAT32 formatted partition (flash drive or internal drive) and have UEFI read that. UEFI only reads FAT32. Some also have a DOS bootable flash drive file to download.

For my desktop I made ESP - efi system partition larger & gave myself read/write permissions so I save updates to it. And Samsung had both Windows or a fully bootable ISO just for my model SSD. It looked like an old DOS screen and just checked SSD drive & updated it.

---

