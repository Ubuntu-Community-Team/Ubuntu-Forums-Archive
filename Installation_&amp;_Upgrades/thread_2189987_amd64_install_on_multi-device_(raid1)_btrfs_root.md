---
title: "amd64 install on multi-device (raid1) btrfs root"
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by splurben on 2013-11-25
I'd like to patch the [FONT=courier new]initramfs[/FONT] to allow Ubuntu to boot on a multi-device ( btrfs-raid1 ) [FONT=courier new]btrfs[/FONT] array.

The main Ubuntu [FONT=courier new]btrfs[/FONT] community page ( [https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs) ) doesn't seem indicate anything to preclude this; I know it normally requires patched 'hooks' in [FONT=courier new]initramfs[/FONT].

I have done this on ArchLinux and Gentoo using [FONT=courier new]mkinitcpio-btrfs[/FONT] with good results, but I have discs prepared which are already in this configuration with Ubuntu on them, but not booting.

[LIST=1]
[*]The community page doesn't specifically mention whether or not this is a supported configuration.
[*]I have had no luck adapting Arch's [FONT=courier new]mkinitcpio-btrfs[/FONT] patch of [FONT=courier new]initramfs[/FONT] to make this work on Ubuntu.
[/LIST]

I want to make sure it *can* work before I try too much harder to get it going.

Does anyone have this working?

Cheers,

Kirk

---

### Post by splurben on 2014-07-11
This works now by default so long as you have BTRFS compiled into your kernel.

---

