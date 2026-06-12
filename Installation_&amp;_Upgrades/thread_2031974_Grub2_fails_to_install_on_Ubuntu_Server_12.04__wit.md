---
title: "Grub2 fails to install on Ubuntu Server 12.04  with RAID5 + Encrypted LVM"
date: 2012-07-22
forum: Installation &amp; Upgrades
---

### Post by tnek on 2012-07-22
Hi!

I recorded my complete installation until failure: [http://www.youtube.com/watch?v=BVe5vja3keo](http://www.youtube.com/watch?v=BVe5vja3keo)

During partitioning I created a software RAID 5 volume spanning three identical disks. On that volume I created an encrypted volume, which I created an LVM inside containing two logical volumes inside a volume group. One logical volume for /boot and one for / (the rest):

[IMG]http://i.imgur.com/Qm4Go.png[/IMG]

When it is time to install Grub to the MBR I get the error Executing grub-install /dev/sda failed. This is a fatal error:

[IMG]http://i.imgur.com/X0Wlw.png[/IMG]

After that I completed the installation without installing a boot loader.

I would greatly appreciate it if someone could help me out. I do want redundancy for /boot so placing it outside the RAID 5 set is not an option.

---

### Post by sir_blargh on 2012-11-01
Having the same problem that you've shown.  Any chance you got it working and have any pointers?  Thanks!

---

### Post by darkod on 2012-11-02
I see EFIboot flag on one of the LVs. Are you using UEFI boot or the legacy bios boot?

If the board has the option, I suggest using legacy only and disabling UEFI boot. That's the first point.

I don't use UEFI and can't help much with that. From what i have read here, if you do insist on using UEFI you have to boot the cd in UEFI mode, not legacy mode. On UEFI boards you will have two dvd-rom devices, legacy and UEFI. Depending which one you select on boot, the cd will boot in that mode. And if you want to use UEFI it has to be UEFI mode.

Second point: I see the disks are 3TB and I assume you are using gpt tables on them. But with gpt grub2 doesn't fit on the MBR because the MBR is smaller, so it needs a small 1MB partiton with NO filesystem (unformatted) and the bios_grub flag set.

So, what I would do:
1. This is a new install and I assume there is no data on the disks. I would boot first with a desktop live cd to prepare the disks with the small partition. And I would use legacy boot as mentioned above. You can create the small partition with the server installer too, but I feel better creating it in live mode. For every of the three disks do this:
```
sudo parted /dev/sda (open the parted prompt)
mklabel gpt (new blank gpt table)
unit MiB (change unit to MibiBytes)
mkpart GRUB 1 2 (make a partition with label GRUB from 1st to 2nd MiB, which means size 1MiB exactly)
set 1 bios_grub on (turn on the bios_grub flag on that partition #1)
exit (exit parted)
```

2. If you want, you can also prepare the partitions for the mdadm raid. In that case you will create the partitions you want and turn on the raid flag on them.

3. After that boot the server cd in legacy mode and continue the install. The bios_grub partitions will already be there, you don't touch them at all, the grub-install will use them. I think grub-install failed because the disks are gpt and there is no bios_grub partition in the screen above. There is no space for grub2.

---

### Post by aurelieng on 2012-11-14
Same problem here with LVM over LUKS over RAID1. I'm testing this in a VirtualBox VM with two 4GB disks: no EFI, no GPT (hence no need to create a bios_grub partition?)

Any idea ? (I can test easily since i have a snapshot of the VM)

Thanks!

Aurel.

---

### Post by darkod on 2012-11-14
> **aurelieng said:**
> Same problem here with LVM over LUKS over RAID1. I'm testing this in a VirtualBox VM with two 4GB disks: no EFI, no GPT (hence no need to create a bios_grub partition?)

Any idea ? (I can test easily since i have a snapshot of the VM)

Thanks!

Aurel.

Do you have a /boot partition outside the lvm/luks? I believe that is a requirement for encyption, the boot files can't be inside.

The /boot can be a raid1 mdadm device itself, but not inside the encrypted part. I might be wrong though.

---

### Post by aurelieng on 2012-11-14
You're right, I created a /boot partition directly on the RAID1, without encryption nor LUKS, and it works perfectly :)

Thanks a lot :)

---

