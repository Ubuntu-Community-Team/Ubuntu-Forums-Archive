---
title: "Ubuntu 22.04 PXE boot -- need help"
date: 2022-12-03
forum: Installation &amp; Upgrades
---

### Post by ajay-saggu on 2022-12-03
Need some help on PXE boot.

LABEL   Ubuntu 22.04
        MENU LABEL UBUNTU_22_04_Virtual
        kernel kernel/ubuntu22/vmlinuz
        append initrd=kernel/ubuntu22/initrd -- ks=http://[COLOR=#333333][FONT=monospace]10.100.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]12.11[/FONT][/COLOR]/ks/ubuntu22.ks ksdevice=bootif ip=dhcp




Trying to PXE boot with the latest Ubuntu 22.04, but seeing this error,
On the console:
DHCPREQUEST tor 10.100.12.160 on ens256 To 255.255.255.255 port 6G? (x1q=0x109 73543
DHCPACK of 10.100.12.160 from 10.100.12.11 (xid=0x4335971b)
bound to 10.100.12.160 -- renewal in 1468 seconds.
Begin: Running /scripts/casper-premount ... done.
[4.733155] XFS (dm-1): Ending clean mount
[4.735276] XFS (dm-1): Unmounting Filesystem
[4.921150] XFS (sdai): Mounting VS Filesystem
[5.139641] XFS (sdai): Ending clean mount
[5.144514] XFS (sdai): Unmounting Filesystem
/init: line 49: can't open /dev/sro: No medium found
/init: line 49: can't open /dev/sro: No medium found

---

