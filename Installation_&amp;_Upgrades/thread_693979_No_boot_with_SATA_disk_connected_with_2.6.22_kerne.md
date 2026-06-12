---
title: "No boot with SATA disk connected with 2.6.22 kernel. No errors, nothing."
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by lolife.se on 2008-02-11
The system boots off the chipset pri/ma IDE disk. The SATA disk is connected to a SiI3512 SATARaid PCI adapter. Right now, whenever I connect the SATA disk, GRUB finds and loads both the kernel and the initrd, and then absolutely *nothing*.

The system boots fine with the SATA adapter clean (no disks connected) so it doesn't seem to be a critical hardware error, right?

The same seem to happen in Annvix 3.0 (currently installed, kernel 2.6.22-something) and Ubuntu Gutsy (tried before, also kernel 2.6.2x-something I believe). Although I don't remember if the symptoms were the exact same, it *did* boot fine with Gutsy, if you downgraded the kernel to Feisty kernel (~2.6.16-something I believe). Is something broken in the new kernels?

The system is a somewhat old Socket A (IWill KK266-R) system with a VIA KT133A chipset, and an AthlonXP 1600+ processor. The KT133A's are a bit quirky, yes, but it has been working perfectly fine before with Linux.

Anyone have any ideas, I'm at a complete loss here. 

GRUB finds the hda disk where it wants it (hd0), the files it needs, aswell as read them OK. You can also access the SATA disk as (hd1) so the BIOS order seems OK. What happens after the initrd command? The kernel won't even start unzip.

Thankful for any help.

---

### Post by lolife.se on 2008-02-11
Here I've been trying for several days, and of course when I decide to post about it in forums, I find the solution short after.

Running the kernel with the edd=off option solved everything. Go figure.

---

### Post by mrsteveman1 on 2008-02-11
The EDD thing would be my first guess, lots of systems (particularly with add in drive cards) hang because the bios doesn't provide good EDD information.

Particularly since the system boots just fine with the card in but not with a drive attached, the difference may be that when there is a drive attached to the card, it inserts its own bios code in order to allow the system to boot from the attached drives. If they didn't do this, the only bootable drives would be the ones directly attached to the motherboard. It seems however that the EDD information gets a bit screwy because of this process and thus the bios reports the root drive incorrectly or perhaps just crashes the kernel.

---

