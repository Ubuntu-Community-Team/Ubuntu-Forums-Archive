---
title: "Errors with btrfs and grub on 24.04"
date: 2024-06-23
forum: Installation &amp; Upgrades
---

### Post by q0p on 2024-06-23
I want to install Ubuntu 24.04 along with windows and Ubuntu 22.04 But after install I can choose windows and Ubuntu 24.04 (no Ubuntu 22.04 menu entry). Why? I have already added this line manually. I want to use btrfs, but during install Ubuntu 24.04 have not choose "use btrfs filesystem" during install. This option is able only for custom partition configuration. If I use btrfs before (during install 22.04) the installer will create mounpoints @ and @home automatically.

---

### Post by yancek on 2024-06-23
Which windows release?  How many physical hard drives?  Are the different installs on different physical drives?  Are they all EFI installs?  What 'line' have you entered manually?  A menuentry in the 24.04 grub.cfg for 22.04?  If both Ubuntu's were EFI installs then 24.04 would have overwritten the ubuntu EFI files with its own.  Did you run sudo update-grub from 24.04 when the install completed?  Can you post some partition infromation using parted or fdisk and indicate which OS is on which partition.

---

### Post by q0p on 2024-07-10
Windows 11
One physical hard drive
They are all EFI installs
```

Disk /dev/nvme0n1: 476,94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: SAMSUNG MZVL2512HCJQ-00B00              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: DBDC2FDA-C33B-4FB5-900B-E094170979E2

Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     206847    204800   100M EFI System
/dev/nvme0n1p2    206848     239615     32768    16M Microsoft reserved
/dev/nvme0n1p3    239616  512710655 512471040 244,4G Microsoft basic data
/dev/nvme0n1p4 997142528 1000214527   3072000   1,5G Windows recovery environmen
/dev/nvme0n1p5 791089152  988753919 197664768  94,3G Linux filesystem
/dev/nvme0n1p6 988753920  997142527   8388608     4G Linux swap
/dev/nvme0n1p7 512710656  791089151 278378496 132,7G Linux filesystem

Partition table entries are not in disk order.


```
p5 - ubuntu 22
p7 - ubuntu 24

```
mount | grep boot
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
```



```
menuentry "Ubuntu_22" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c99912a8-02c1-4039-8bf3-6a6ea2076988' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod btrfs
    search --no-floppy --fs-uuid --set=root c99912a8-02c1-4039-8bf3-6a6ea2076988
    linux    /@/boot/vmlinuz-6.5.0-41-generic root=UUID=c99912a8-02c1-4039-8bf3-6a6ea2076988 ro rootflags=subvol=@  quiet splash $vt_handoff
    initrd    /@/boot/initrd.img-6.5.0-41-generic
}
```

---

### Post by q0p on 2024-07-10
> Did you run sudo update-grub from 24.04 when the install completed
Yes, but Ubuntu 22 wasn`t found.
I copied lines from /boot/grub/grub.cfg from 5th partition to enable boot to ubutntu 22

---

