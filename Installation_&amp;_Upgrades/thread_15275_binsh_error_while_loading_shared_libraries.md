---
title: "/bin/sh: error while loading shared libraries"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by Gully Foyle on 2005-02-13
Hi all,

I'm attempting an install onto an old laptop with no CD drive. I attached the laptop drive to my desktop as HD0 (on a standard IDE channel with no other HD attached to the machine), and installed a base system onto it from CD. Booting the desktop machine from the laptop drive works fine. Transferring the disk back to the laptop results in a boot failure. After the "Uncompressing Linux... Ok, booting the kernel." message, I get the following 3 lines:

"ACPI: Unable to locate RSDP" - Fair enough, it's an old laptop, and doesn't have ACPI support.

Then:
"/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory"

Then a kernel panic:
"Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)".

From reading the support fora here I get the impression that either the initrd is wrong or that there is some scsi/dma setting that I need to fiddle with, but I have no clue where to start, since i've never used grub before...

Thanks in advance for any responses.

---

### Post by Gully Foyle on 2005-02-13
Replying to myself to note what my current grub boot script looks like:

root (hd0,0)
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

As I said before, any suggestions welcome.

Thanks.

---

### Post by Gully Foyle on 2005-02-14
And again replying to myself to say that the initrd and linuz files are in the correct place as pointed to by the grub scripts. I've booted TomsRTBT single floppy linux and mounted the hda1 partition on the laptop, and as far as I can see, it contains everything in the right place. Just can't find it on boot. :?

---

