---
title: "Failed dual boot with Fedora"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by cub on 2018-04-27
I have prepared my laptop to run both Fedora and Ubuntu. I have split the HDD and installed Fedora 27 earlier on the first partition. Today I installed 18.04 on the free space. However my GRUB menu is missing and it boots directly to Ubuntu without any way to boot into my Fedora. The laptop runs old Bios so nu UEFI. I have run 'sudo update-grub' but no change.

This has never been a problem before. I used to run several Linux installations on the same computer before.

Any ideas?

sudo update-grub:
```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.15.0-20-generic
Found initrd image: /boot/initrd.img-4.15.0-20-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

fdisk -l:
```
Disk /dev/sda: 167,7 GiB, 180045766656 bytes, 351651888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x3eaa0932

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048   2099199   2097152    1G 83 Linux
/dev/sda2         2099200 165271551 163172352 77,8G 83 Linux
/dev/sda3       165273598 351649791 186376194 88,9G  5 Extended
/dev/sda5       165273600 262928383  97654784 46,6G 83 Linux
/dev/sda6       336027648 351649791  15622144  7,5G 82 Linux swap / Solaris
/dev/sda7       262930432 336015359  73084928 34,9G 83 Linux

Partition table entries are not in disk order.

```

Ubuntu is installed on sda5, ubuntu home is sda7 and swap on sda6. Fedora is using the other Linux parts. The Fedora drives are encrypted and I used to provide a password at boot, which I don't have to do any longer (which is bad).

---

### Post by cub on 2018-04-27
So, maybe a step forward.

First I edit /etc/default/grub and changed to show the grub menu at boot. I added lvm2 support in Ubuntu. I then mounted the encrypted LUKS. When I then ran update-grub it found the Fedora installation. Success, I thought. When I reboot I can choose Fedora in the Grub menu but the boot hangs. No go, so far ...

---

### Post by cub on 2018-04-27
Actually, it didn't hang. It was waiting for me to enter the passphrase for Luks, just no information or hint it was a prompt. So, kind of problem solved. Not pretty, but it works.

---

