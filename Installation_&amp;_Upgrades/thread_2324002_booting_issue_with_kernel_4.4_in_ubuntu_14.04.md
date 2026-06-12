---
title: "booting issue with kernel 4.4 in ubuntu 14.04"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by Karl_May on 2016-05-10
Hi there.


I have an issue with kernel 4.4 in ubuntu 14.04. While booting with kernel 4.2.0-35 is easy, booting with all kernels above that (4.4+) fails because the boot partition cannot be be found. The boot process then drops to shell:
```

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
-Check rootdelay ....
-Check root ...

```

The system runs on an ssd as installation media and an hd as a data media (mounted at home while booting) and boots in UEFI mode.
The installation was done via kubuntu installer selecting lvm and using the whole ssd as installation media. Adding the hd to crypttab and fstab was done manually.

The output of blkid is:
```

/dev/nvme0n1p1: UUID="9C01-CB32" TYPE="vfat"
/dev/nvme0n1p2: UUID="7cbe06ab-1537-4579-a250-86fdfa606b01" TYPE="ext2"
/dev/nvme0n1p3: UUID="wVjBzG-F0KQ-ckIO-O6Qp-MTaw-M61k-pc549Y" TYPE="LVM2_member"
/dev/sda1: UUID="dkjuOP-s824-8J8p-j5ch-YFMP-HMlT-XmMTJC" TYPE="LVM2_member"
/dev/mapper/kubuntu--vg-root: UUID="bb919e3d-81df-4a86-b45d-d5a6330e349c" TYPE="ext4"
/dev/mapper/kubuntu--vg-swap_1: UUID="96f23482-8c01-4756-9df6-4ed934bbaf34" TYPE="swap"
/dev/mapper/data-data: UUID="829a1cbe-3952-48dc-b4f9-2c70464c9a92" TYPE="crypto_LUKS"
/dev/mapper/data_crypt: UUID="167c5b31-6794-43b4-90db-6f962b18d667" TYPE="ext4"

```

nvme0n1p1 is the UEFI partition, nvme0n1p2 the boot partition, and nvme0n1p3 harbours / and swap. sda1 is encrpyted and mounted at /home at boot.

I read somewhere that kernel 4.4+ cannot deal with device names like "nvme...", however posts on that topic are rare and I don't really have an idea how to proceed.
I don't think that updating to 16.04 will solve the issue because kernel 4.4+ is supposed to run under 14.04 as well.

Any suggestions??

Thank you very much

Cheers

Karl

---

### Post by Bucky Ball on 2016-05-10
Where did you get the kernel and how are you trying to install it?

14.04 still boots fine from other kernels? I know nothing about LVM but that could certainly have something to do with it.

---

### Post by Karl_May on 2016-05-10
Everything came via 14.04 repositories. Everything installed via apt-get. Didn't get any error messages when running update-initramfs and grub-update. 14.04 boots on all kernels including kernel 4.2.0-35. No boot on kernel 4.4.

Cheers

---

