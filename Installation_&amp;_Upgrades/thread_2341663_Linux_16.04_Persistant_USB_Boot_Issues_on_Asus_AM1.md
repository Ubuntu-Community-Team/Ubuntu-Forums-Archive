---
title: "Linux 16.04 Persistant USB Boot Issues on Asus AM1A-IM"
date: 2016-10-30
forum: Installation &amp; Upgrades
---

### Post by cupcake36 on 2016-10-30
Hi guys, I'm having some issues trying to boot into my Linux USB system on the Asus board.

Works fine on another PC I have running a Gigabyte board.

The Asus board is the AM1A-IM

For clarity this is what I've done so far.

Fast Boot = disabled

CSM = enabled

Boot Device Control = Legacy OpRom

Secure Boot = Disabled (also deleted secure boot keys)

OS Type = Other OS

Boot Option 1 = USB Linux Drive

Running latest BIOS version for the board.

All that happens is the rig keeps booting into the BIOS, it won't actually load the OS from the pen drive.

As I said, everything works fine on a Gigabyte board.

Reason for doing this is I'm trying to run the Asus rig as my media server.

---

### Post by ubfan1 on 2016-10-30
Do you get to the bootloader on the pendrive?  That would be the syslinux one for a legacy boot, although setting CSM may be an uncertain way to accomplish that.

---

### Post by cupcake36 on 2016-10-31
> **ubfan1 said:**
> Do you get to the bootloader on the pendrive?  That would be the syslinux one for a legacy boot, although setting CSM may be an uncertain way to accomplish that.

When I use the machine with the Gigabyte board I do, and I can choose between my Win 10 OS and Linux, however when I plug the pen drive into the Asus board, I don't get any boot loader at all.


Really confused by it all when it works fine in one system but not another.

---

