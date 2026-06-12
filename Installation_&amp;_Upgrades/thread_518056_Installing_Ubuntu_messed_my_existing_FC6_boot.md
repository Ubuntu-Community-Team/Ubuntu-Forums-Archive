---
title: "Installing Ubuntu messed my existing FC6 boot"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by kcramakrishna on 2007-08-05
I had FC6/WinXP/Suse running on my laptop(Compaq V6120US) and installed Ubuntu 7.04 a couple of days back.

Now I can't boot to FC6. Suse and Windows were **not** affected.
FC6 is the one affected and is the last entry in the grub file.
The error is something like this:
kernel panic - cannot find VFS (or similar), 
give an option like "root="

I tried some basic grub stuff but nothing seems broken. Attached is the grub file.
Another funny thing I noticed is that there seems to be no /boot/grub/menu.1st in the FC6 directory. It has only some splash.gz... file. I am sure Ubuntu cannot have deleted those files.

Used to be a techie but have forgotten quite a bit now. So please be gentle. This prob is different from the other threads with similar sounding topics hence the different thread.

==============================================
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ce870218-5d9c-4eef-bfe1-701181df0b65 ro noapic nolapic splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ce870218-5d9c-4eef-bfe1-701181df0b65 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           openSUSE 10.2 (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.18.2-34-default root=/dev/sda2 vga=0x317 resume=/dev/sda5 splash=silent showopts
initrd          /boot/initrd-2.6.18.2-34-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Failsafe -- openSUSE 10.2 (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.18.2-34-default root=/dev/sda2 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
initrd          /boot/initrd-2.6.18.2-34-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title           Fedora Core release 6 (Zod) (on /dev/sda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.18-1.2798.fc6 root=/dev/sda3 noapic
savedefault
boot

---

