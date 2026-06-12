---
title: "Boot messages show after splash"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by driveoldford on 2011-08-21
Re: Boot messages after splash screen.
Hi ALL:
I am trying to get Ubuntu (10.04) to boot like it does if I select SuSe 11.4 from grub.
Specifically, after the splash screen, the boot goes to f1 console and the boot messages scroll past (and I can see was happening).
The entry in /boot/grub/grub.cfg looks like this:
"menuentry "Desktop -- openSUSE 11.4 - 2.6.37.6-0.5 (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 9bd5e37b-dfb9-437e-9015-f9a10bf0159b
    linux /boot/vmlinuz-2.6.37.6-0.5-desktop root=/dev/disk/by-id/ata-ST9120823AS_5NK0KPQJ-part6 resume=/dev/disk/by-id/ata-ST9120823AS_5NK0KPQJ-part5 splash=silent quiet showopts vga=0x345
    initrd /boot/initrd-2.6.37.6-0.5-desktop"
I tried pasting the kernel parameters into grub.cfg at the Ubuntu entry:"splash=silent quiet showopts vga=0x345", but that did not work, and, I know that I am not supposed to modify this file anyway.
Does anyone have any idea about how I can get Ubuntu to boot like my SuSe installation?

---

