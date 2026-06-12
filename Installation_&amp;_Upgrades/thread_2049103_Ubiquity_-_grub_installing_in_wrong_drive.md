---
title: "Ubiquity - grub installing in wrong drive"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by sandyd on 2012-08-27
Ive just saw a thread where the OP replaces Ubuntu on a second drive, and Ubiquity installs grub on the second drive as well. This obviously results in Ubuntu not booting, if the version of Ubuntu that they are replacing has a older grub version (even a few minor versions off).

Shouldn't Ubiquity be automatically selecting the main HDD (i.e. /dev/sda) for grub installation, rather than the drive that Ubuntu is going on? Im not asking for Ubiquity to remove the option to select the drive that grub goes on, but to select the *correct* drive by default.

Can someone test this behaviour?

Thanks!

Note that this might be the same with any Ubuntu install on a second HDD - I wouldn't know since I don't use the GUI installer.

---

### Post by oldfred on 2012-08-28
I have seen discussion both ways.

If an external drive you really do want grub2's boot loader on the external. I normally suggest installing grub to the same drive as the install and changing BIOS to boot that drive. Then each drive can boot a system on that drive if other drive fails.

The old way always was to just install to sda. But some flash drives get mounted as sda, so those users install grub to the installer flash drive. I had not seen that it has changed.

I do not think they should have an auto install location, but users in most cases do not know where to install, so it is a problem either way.

---

