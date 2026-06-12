---
title: "Secure Boot &amp; LUKS"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by highbomber on 2013-05-16
Greetings,

I am having difficulty setting up SecureBoot installation. I believe my laptop is capable, because when SecureBoot is enabled I am still able to boot onto the Ubuntu 13.04 Live disk.

I have a special setup, however. Windows is _not_ installed, but the drive is using a GPT partition table. UEFI is working. My partitions are:

/dev/sda1: FAT32 EFI     512MB
/dev/sda2: ext2   BOOT  512MB
/dev/sda2: LUKS  LUKS  remaining ~465GB

Inside LUKS is an LVM:
SWAP: 16GB
/dev/mapper/ubuntu-root: root btrfs remaining ~450GB

Sub volumes include @ (root) and @home.

Firstly, unsigned kernels boot. Currently I am running 3.9.0-1-generic (x86_64). When SecureBoot is disabled, the *signed* kernels still do not boot. Signed kernels are unaware of my LUKS partition, do not engage in its decryption, yet I receive an error that "/dev/mapper/ubuntu-root" is unavailable. Furthermore, if I try to update initramfs:
```
update-initramfs -u -k all
```
It ignores the signed kernel.

I hope that if I can update initramfs and the signed kernel than I will be able to boot using the signed kernel (at least with SecureBoot disabled).

Any help is greatly appreciated!

---

### Post by highbomber on 2013-05-24
Bump.

I will also point out: signed kernels *work*. When booting with a signed kernel my password for the LUKS partition is not requested.

---

### Post by darekch on 2013-05-24
Can you give more information how you SecureBoot works? You mix several states signed and unsinged kernels with secureBoot enabled/disabled, I'm little confused in that.

May I point out that if update-initrams -u -k all doesn't see you signed kernels then signed kernel will not see your luks partition and it won't prompt for password and decrypt. This is how it is in normal configuration without secure boot, guess it can be similar with secure boot.

---

