---
title: "ecryptfs: passphrase prompt not visible in boot sequence"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by Ivo_Wever on 2010-06-20
Since upgrading from Karmic to Lucid, the ecryptfs passphrase prompt requesting me to enter my passphrase, so it can unlock and mount my /home, isn't visible anymore. When it should be shown, the screen seems to switch to X, but it subsequently stays blank and booting doesn't proceed. At that moment, the prompt is active: I can enter the passphrase, press Enter and the boot process proceeds.

I've removed the 'quiet splash' from /etc/default/grub, but that only affects what happens before the screen goes blank.

[The Lucid  ReleaseNotes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes") mention that

> **Encrypted partitions must be listed in /etc/fstab**
Users who have configured any encrypted partitions in /etc/crypttab to start at boot time (i.e., not using the noauto option) should make sure that the filesystems on these volumes are listed in /etc/fstab. Otherwise, the passphrase prompt is not guaranteed to be displayed at boot time.

**LVM filesystems should be listed in /etc/fstab by name**
In general, filesystems are listed in /etc/fstab by UUID rather than by device name, to ensure that the filesystem can always be found reliably. If you are mounting a filesystem located on LVM, however, it is recommended that you list them in /etc/fstab by device name, not by UUID, because UUIDs are not unique if LVM snapshots are used, which can result in wrong filesystems being mounted at boot. (563902)

I've tried adding the encrypted partition to fstab, but it doesn't make a difference. This is not unexpected, because the encrypted /dev/mapper/sda1_crypt is part of the LVM partition /dev/mapper/photon-root, which is already present.

My /etc/crypttab and /etc/fstab:
```
sda1_crypt /dev/disk/by-uuid/bfac35d7-8fbf-4487-8515-43444d065bd8 none luks
cryptswap1 /dev/mapper/photon-swap_1 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
```

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/photon-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=60c0dc14-7aa6-4782-ab0d-a09fc9bdb22e /boot           ext2    defaults        0       2
#/dev/mapper/photon-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```
Does anyone know how I can fix this?

---

