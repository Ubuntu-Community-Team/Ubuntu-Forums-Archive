---
title: "uefi bootloader unlocking multiple luks crypto disks"
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by bugrider2 on 2017-04-01
_**[FONT=courier new]Disk layout:[/FONT]**_
[FONT=courier new]nvme0n1p1 512MB fat32 EFI System partition
nvme0n1p2 512MB ext2   /boot
nvme0n1p3     8MB luks   ext2  (see below about the meaning of this partition)
nvme0n1p4   ~1TB luks   LVM
nvme1n1p1   ~1TB luks  LVM
[U][B]
LVM layout:[/B][/U]
PVs:[INDENT]/dev/mapper/nvme0n1p4_crypt
    /dev/mapper/nvme1n1p1_crypt
[/INDENT]
 VG:[INDENT]ubuntu-vg has both PVs
[/INDENT]
 LVs in ubuntu-vg:[INDENT]swap_1 as swap
    root   as /
    home   as /home
[/INDENT]
 
After booting from Ubuntu 16.04.2 liveCD, the above disk/LVM configuration was set up manually.
The three luks containers have the same key passphrase.
Original plan was to have a keyfile with that passphrase on nvme0n1p3 and use that to unlock nvme0n1p4 and nvme1n1p1, in order not to have to enter three passphrases.

After that ubiquity installer was started and the system was installed correctly, using the partitions as intended by the manual setup.
Except for the crypto setup of course and as expected.

[U]After install and as su:
Manually mount:[/U][INDENT]root at /mnt/root2
               nvme0n1p2 at /mnt/root2/boot
               nvme0n1p1 at /mnt/root2/boot/efi
[/INDENT]
 chroot /mnt/root2
generate a suitable /etc/crypttab with the entries for the three disks (initially without keyfile support)
mount -t proc proc /proc
mount -t sysfs sys /sys
and then do
update-initramfs -u

and this fails with
WARNING: no ldd around - install libc-bin

ldd of course is NOT missing in the chroot environment. It is in /usr/bin/ldd

I am a bit lost here. Searched around and tried some things. But up to now I don't have a clue how to fix this.
I am probably missing a necessary mount in the chroot, but couldn't figure it out.

**_Anybody having an idea what is going wrong?_**
[/FONT]

---

### Post by bugrider2 on 2017-04-01
I managed to get over the mkinitramfs script error by commenting out the lines that check for ldd.
update-initramfs -u
was then successful.

However, then booting the system (with "quiet splash" removed from the grub command list) does not get far: Empty vga screen, no text output.. dead.

Next attempt: Edit the grub command list..
After 'insmod ext2', add 4 lines:

insmod luks
cryptomount (hd1,gpt3)
cryptomount (hd1,gpt4)
cryptomount (hd2,gpt1)

and remove "quiet splash".

STRANGE result when booting:

vga screen with text output:
Enter passphrase for hd1,gpt3:
<enter passphrase, then after a few seconds...>
Slot 0 opened
<then the second cryptomount for hd1,gpt4 is skipped!!>
Enter passphrase for hd2,gpt1:
<enter passphrase, but after that nothing happens anymore.. dead>

So I tried again without the above first mount for gpt3, as it is not mandatory for the system.
It then asks for the passphrase for hd1,gpt4 and then for hd2,gpt1, but after that again, nothing happens anymore

[note that this is not a problem with the passphrase, because I can unlock the disks when booted from liveCD]

So, I am even more clueless than before...  any ideas welcome...

---

