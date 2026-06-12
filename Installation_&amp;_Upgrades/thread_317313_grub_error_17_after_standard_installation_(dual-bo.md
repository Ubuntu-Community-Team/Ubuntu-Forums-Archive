---
title: "grub error 17 after standard installation (dual-boot)"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by renem on 2006-12-12
Hi,

I spent some hours to look for a solution for my problem in the internet, but I haven't found any, so I finally decided to post my problem here:

- Starting with a previous windows installation with C: and D: I resized D: to provide space for ubuntu at the end of my one and only 250G hard disk.
- As hda3 I created 512M swap space, as hda4 a 10G EXT3 partition for /.
- Ubuntu seemed to install fine, but after reboot "GRUB error 17" appeared (fixmbr and fixboot from XP CD fixes this and windows boots again).

I tried the different solutions found in the internet such as update-grub, grub-install, root (hd0,3), setup (hd0,0), changing BIOS settings to LBA or LARGE... The problem remained always the same.

Maybe there's one hint: when doing setup (hd0,0) after root (hd0,3) grub says something like "embed ... didn't work - not fatal" before "install ... succeeded". find /boot/grub/stage2 yields (hd0,3).

My configuration so far (hda3 is normal swap, hda4 is standard ext3):

fdisk -l:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/hda2            2612       28999   211961610    7  HPFS/NTFS
/dev/hda3           29000       29064      522112+  82  Linux swap / Solaris
/dev/hda4           29065       30401    10739452+  83  Linux

menu.lst:

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash locale=de_DE
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

device.map:

(hd0)	/dev/hda

Any good idea? :-)

---

### Post by bernied on 2006-12-12
The setup command should be 
setup (hd0) 
not 
setup (hd0,0)
(hd0) refers to the master boot record on the disk, (hd0,0) refers to the boot record in the first partition - the windows partition. I fear that you may have damaged your windows install with this command. A Windows recovery disk should be able to fix this if it is true, though it will most likely 'fix' your master boot record as well.

Having said that, it is possible that you were originally unable to boot because your BIOS won't boot so far into the disk. Historically their was some limitation in disk size that you may be suffering from. You asked for a good idea, I'm not sure that this one was....

---

### Post by renem on 2006-12-12
You're right, it is/should be setup (hd0). Which means that some of what I tried wouldn't have had any effect...

But the fact that the original standard installation process made boot-up fail with grub error 17 shows that principally grub had been installed into the MBR, not first partition.

I also tried to use boot.ini from windows to boot up ubuntu but it makes the computer reset, shortly after showing the word GRUB_.

For now I created a boot partition /dev/hda1 which should make things work. In the beginning this is what I didn't want because of the problems it might have had on windows C:...

I'll give it a try later with this setup because the last attempt didn't succeed: after correcting the partition order via fdisk windows wouldn't start. Like in the good old times. Man, I'm glad I've moved to a single boot system only (with SUSE, now Kubuntu) with my other computer... :-/

---

