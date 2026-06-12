---
title: "help!  windows killed ubuntu!!!"
date: 2006-10-06
forum: Installation &amp; Upgrades
---

### Post by tibbar on 2006-10-06
i'm writing here as a last resort...

here's the background, setup:

IDE0 master: cdrom
IDE0 slave : hard-disk - Ubuntu Dapper
IDE1 master: hard-disk - win xp
IDE1 slave: hard-disk (data only)

it was working fine with grub as the bootloader...until one day i got a message from windows "windows has recovered from a serious error".  i thought nothing of it until rebooting and finding it had taken over the MBR of the ubuntu harddrive...nice, thank you Microshite...

i then ran the dapper live cd and did:

sudo bash
mkdir /mnt/root
mount -t ext3 /dev/hdb3 /mnt/root
mount -t proc none /mnt/root/proc
mount -o bind /dev /mnt/root/dev
chroot /mnt/root /bin/bash
mount -t ext3 /dev/hdb3 /boot

and then either:

grub
find /boot/grub/stage1
root (hd0,2)
setup (hd0,2)

or:
grub-install /dev/hdb3

in both cases it tells me its been successful, so i reboot...

then i get message "missing ntldr".

i tried using xp's recovery console and did fixmbr / fixboot
but this failed to get windows to boot either (same error)..i was thinking of using xp's boot menu if all else failed.

i've tried using dd ... 512 to clean the MBR and repeat above, with no luck.

here's my fdisk -l output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            4467        5280     6538455    5  Extended
/dev/hdb2            5281       19457   113876752+  83  Linux
/dev/hdb3   *           1        4466    35873113+  83  Linux
/dev/hdb5            4467        5280     6538423+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       14592   117210208+   7  HPFS/NTFS


im out of ideas...can anyone help?

thanks.

---

