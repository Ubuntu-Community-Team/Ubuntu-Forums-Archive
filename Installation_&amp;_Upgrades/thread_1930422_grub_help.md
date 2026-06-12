---
title: "grub help"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by sanchini on 2012-02-23
I am trying to get ubuntu to boot from USB from an intel mac with efi loader, traditionally not possible.

By adding a recomiled grub2 into /efi/boot/bootx64.efi I can now get it to happily load up any iso that I leave in that folder named boot.iso. This is great, but I can't get it to have perseverence in iso form.

If I rename the iso and drop a grub.cfg in there the grub in the bootx64.efi reads and displays it, so I can't see any reason why I can't now install ubuntu onto the drive using unetbootin (set with perseverance ) than alter than grub config to boot my linux image - but I'm having trouble with grub.

my pen looks like:

/casper/filesystem.manifest
/casper/filesystem.manifest-remove
/casper/filesystem.size
/casper/filesystem.squashfs
/casper/initrd.lz
/casper/vmlinuz

as noraml in ubuntu.

Can anyone give me a grub pointer to make this boot from usb? All examples look for the iso, not the files required it seems.

Thanks.

---

