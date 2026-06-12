---
title: "Grub boot loader failed to install"
date: 2018-06-22
forum: Installation &amp; Upgrades
---

### Post by connappted on 2018-06-22
Hi Guys,

hoping that you could help me fix my ubuntu installation. Ive tried butting my bios boot settings into legacy and that finally allowed me to install using nomodeset.

Now halfway through install I got the message that grub boot loader failed to install and that I would not be able to Boot:

[http://paste.ubuntu.com/p/sT6Jdy9D2g/](http://paste.ubuntu.com/p/sT6Jdy9D2g/)

Bootrepair info gave me this link please help!

regards,

Steef

---

### Post by Dennis N on 2018-06-22
Your sda disk is partitioned with GPT partition table. You need a bios boot partiton in order to install Grub boot loader in BIOS mode on a GPT partitioned disk.

General Information:
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)

---

### Post by connappted on 2018-06-22
Do you have a link on how to do this, how much space I shoud use?

And on which SDA should I make such a partition?

---

### Post by Dennis N on 2018-06-22
It's easy to make. The attached image of gparted shows the bios boot partition which is sda2. You make a 2 mB partition that is left unformatted. Set the partition flag to bios_grub. That's all.

---

### Post by oldfred on 2018-06-22
You must have partitioned drive from Windows in UEFI boot mode.
It created the Windows required System Reserved partition. That is similar to bios_grub but much larger as unformatted space for Windows use.

I would convert System reserved to an ESP - efi system partition FAT32 with boot flag. for future use in case you want to change to UEFI boot.
You can shrink sda1 by 3MB and add a 1MB unformmated partition with bios_grub there.

---

