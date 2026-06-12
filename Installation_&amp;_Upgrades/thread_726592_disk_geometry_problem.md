---
title: "disk geometry problem"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by kai111 on 2008-03-16
can no one help me fixing this disk geometry problem?
[COLOR="Sienna"]
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
Current partition structure:
Partition Start End Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
1 P HPFS - NTFS 0 1 1 2464 239 63 39599217 [Preload]
2 * Linux 2465 0 1 7091 254 63 74332755
3 E extended 7092 0 1 7295 254 63 3277260
5 L Linux Swap 7092 1 1 7295 254 63 3277197[/COLOR]

this is the testdisk output it get

when i change the head number to 240 it says:

[COLOR="Sienna"]Disk /dev/sda - 60 GB / 55 GiB - CHS 7752 240 63
Current partition structure:
Partition Start End Size in sectors

1 P HPFS - NTFS 0 1 1 2618 239 63 39599217 [Preload]

Warning: Bad ending head (CHS and LBA don't match)
2 * Linux 2619 15 1 7535 59 63 74332755

Warning: Bad starting head (CHS and LBA don't match)
3 E extended 7535 60 1 7751 239 63 3277260

Warning: Bad starting head (CHS and LBA don't match)
5 L Linux Swap 7535 61 1 7751 239 63 3277197

Warning: Bad starting head (CHS and LBA don't match)[/COLOR]

what on earth is the problem

I heard that geometry actually doesn't matter because nowadays files only depend on lba addressing, but i would still like to fix it because i don't know what problems it might cause.

I also heard sth about telling the linux kernel what head numbers to use.

Does anyone know?

---

### Post by Fire_Chief on 2008-03-18
You may want to check your motherboard BIOS setting for the hard drive. Sometimes it will let you specify the addressing method (CHS / LBA / Other). If the drive is having errors when set to CHS, try changing it to LBA and see if Linux likes that better.

Cheers!

---

