---
title: "&quot;missing operating system&quot; when booting from SSD of hybrid disk"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by kc600 on 2013-01-16
I'm trying to get my hybrid-disk (SSD+HDD) machine to boot from the SSD, but i get a message saying "missing operating system" when booting. 

The machine is a new Lenovo Thinkpad S430 with 16Gb SSD and 500Gb HDD. I installed Ubuntu from USB stick on the whole disks, wiping out the existing partitions. I put / and /boot on the SSD (/dev/sdb), and the rest (/home, /usr, /var, /tmp, swap, /srv, /opt) on the HDD (/dev/sda). The BIOS is configured to first try booting from SSD, then USB stick, then CD (no HDD).

When booting Ubuntu from USB, i can see both the HDD and SDD. Partitions are not empty, indeed the install seems to have run well. I've tried using gparted to flag the / partition (/dev/sdb1) with "boot" but no effect. Same for /boot partition (/dev/sdb5). Both filesystem types are ext4.

---

### Post by darkod on 2013-01-16
That is usually a bios message, not grub/ubuntu message. It means you have no boot flag set. Linux doesn't use a boot flag but windows does and many computers are designed to give an error if they can't see a boot flag on one of the partitions. It doesn't even try to boot the computer.

Just use Gparted from live mode and put a boot flag on the /boot partition for example. In Gparted you need to right-click the partition and select Manage Flags.

It should be fine after that.

---

### Post by kc600 on 2013-01-17
Darko, i did just that - see what i wrote above.

---

### Post by darkod on 2013-01-17
Try putting the boot flag on any primary partition of sda, not sdb. In a hybrid setup the ssd is usually only a cached drive so maybe it expects the boot flag on sda.

If that doesn't work, I don't have other ideas but that message is definitely from bios, not ubuntu.

---

### Post by kc600 on 2013-01-17
Danko, thanks for your reply.

I did a complete new install, and it worked now. I think i may have improperly set the HDD as the boot disk on the first install. I now set this to the SSD, and it prompted me to create an efi partition there. On my first attempt, there was no such partition.

---

### Post by darkod on 2013-01-17
Well, you never mentioned you are using the new UEFI boot. That's a whole different ball game. :)

If you ask me it was better to disable the uefi boot if bios gives you the option, before you did a reinstall. That way it would have installed in legacy mode.

But this is fine too, if it works for you.

---

