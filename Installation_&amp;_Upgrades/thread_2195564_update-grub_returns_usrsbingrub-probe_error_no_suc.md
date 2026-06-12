---
title: "update-grub returns /usr/sbin/grub-probe: error: no such disk. | xen, raid, luks, lvm"
date: 2013-12-24
forum: Installation &amp; Upgrades
---

### Post by craig0927 on 2013-12-24
I'm trying to get Xen working on a fresh install of Ubuntu 12.04, but I'm not able to get grub-update to generate a new grub.cfg with the Xen menu items due to this grub-probe error.    It sounds like it may be due to this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1027951](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1027951).  Just wondering if anyone might suggest a work around that would allow me to run update-grub successfully with a LUKS encrypted root...or somehow boot into Xen with an encrypted dom0 lvm on raid.

My /boot partition is on an unencrypted raid1, /dev/md0.
dom0 / and swap are on a luks encrypted lvm, /dev/mapper/xen-dom0.....on a raid0...or /dev/md1...or /dev/dm-2...

I was following the instructions at [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen).
I've attached my /etc/default/grub [ATTACH]248868[/ATTACH] and /boot/grub/grub.cfg [ATTACH]248869[/ATTACH] for reference.  

I have tried differnt values for GRUB_CMDLINE_LINUX_DEFAULT, including:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="cryptopts=target=md1_crypt,source=/dev/mapper/xen-dom0,lvm=xen-dom0 quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="cryptopts=target=md1_crypt,source=/dev/mapper/dm-2,lvm=xen-dom0 quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="cryptopts=target=md1_crypt,source=/dev/mapper/md1,lvm=xen-dom0 quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="cryptopts=target=md1_crypt,source=/dev/mapper/md/1,lvm=xen-dom0 quiet splash"

All variations result in teh following output:

```
user@xen:~$ sudo update-grub
[sudo] password for user: 
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found memtest86+ image: /boot/memtest86+.bin
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
done

```

---

