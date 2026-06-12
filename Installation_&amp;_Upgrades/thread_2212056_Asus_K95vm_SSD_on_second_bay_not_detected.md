---
title: "Asus K95vm SSD on second bay not detected"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by tronch on 2014-03-19
K95vm SSD on second bay not detected

Hi, I tried to install a second Kingston 240GB SSD hard disk on my K95V laptop, but, after install Ubuntu 13.10 OS on it, the boot doesn't work.

In BIOS I can correctly see the SSD HDD on SATA list P1 (P0= primary HDD, P1=SSD HDD, P2=CD/DVD ), but I can't see it on bootable device (I see only P0 and P2 devices)

During Ubuntu installation I see the SSD with no problem and I can select it as HDD for the installation

In windows (OS in the primary HDD) I can see the SSD disk  but, obviously, I can't see the data....

What am I doing wrong?


Thanks.
tronch

---

### Post by ubfan1 on 2014-03-19
Which devices are boot devices is a function of the BIOS.  But you should be able to boot grub off the first disk, and run an installation on the second disk.

---

### Post by tronch on 2014-03-20
No way....

1) I tried to disconnect Primary HDD and leave only SSD on second bay.
2) I installed Ubuntu 13.10 on SSD 240Gb  on Ext4, no swap partition mounting point "/" (I can see very well during installation...)
3) the installation proceed with no errors
4) whe I reboot the PC, this is the message: [https://www.dropbox.com/s/pdix7z961tc1wht/20140319_232618.jpg](https://www.dropbox.com/s/pdix7z961tc1wht/20140319_232618.jpg)

Any ideas?

Thanks.

---

### Post by ubfan1 on 2014-03-20
Sometimes grub and BIOS have a different numbering on the disks, and to make matters worse, when installing grub the first time from live media, the disk numbering is usually one too high because of the USB install media. DVDs usually don't cause this problem because they are named differently, but who knows?  Anyway, from the live media run grub, and type c for command line. Then use the TAB key for completion, to get the disk numbers -- a command like     set root=TAB   or set root=(hdTAB   The disks seen should be offered in a list.  hd0, hd1, ...  start filling in the disk and then type tab again, the partitions should then be shown.  You can usually tell which disk you are looking at by the partitions.  If not, you can keep going to the files on a partition to tell.  Now when you get the disk number used by grub (assume hd1), take a look at the grub config file in /boot/grub/grub.cfg  (or for UEFI machines start at the EFI partition and /EFI/ubuntu/grub.cfg, but it usually then brings in the other file, so check both).  See what disk it uses -- the UUIDs used should be ok, but hd? and sometimes /dev/sd?? devices may be wrong.  Try to match devices ( you can edit the grub.cfg file or try at the actual boot to change things with the e for edit key (instructions on screen for editing).  At  the first successful boot, run sudo update-grub to fix things (hopefully).  I tried a second disk in a DVD caddy, and had boot problems, but of a different nature.  The DVD caddy disk was seen as a hard disk, and it was first in the boot sequence (when no usb was present), but any access to the disk (even a set root= in the grub.cfg file, would turn on the disk light and freeze everything.  Nevertheless, with a usb (first in the boot sequence), and a grub.cfg file which did not directly reference the DVD caddy disk, I could boot an SSD in the main slot, then successfully mount the DVD caddy disk and use it.

---

