---
title: "Grub 2 error:  Kernel must be loaded first"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by v1nsai on 2009-12-19
I just installed Fedora Core 12 on my system, and instead of letting it install it's nice, comfy and dependable legacy grub boot loader, I decided to try to add it to Grub2.  I copied my Ubuntu entry from /boot/grub/grub.cfg, put it in /boot/grub.d/40_custom and changed the kernel, initramfs and UUID to match Fedora, but when I tried to boot from it I get "the kernel must be loaded first".

This may be because I don't understand Fedora (that's why I'm installing it) but I'm sort of stumped about what I could be doing wrong.  I pulled the UUID from my ubuntu /dev/disk/by-uuid because I couldn't find that folder in the Fedora partition.

Would appreciate if someone could tell me what I'm doing wrong, I'm tired of reading Grub2 docs.

Here's the entry in /etc/grub.d/40_custom:
```

menuentry "Fedora 12" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 5ab69ff7-468c-4736-b535-e5416c2a6562
	linux	/boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=693e59f9-9ad8-4f18-aed3-10ae0694499c ro   quiet splash
	initrd	/boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}
```

---

### Post by darkod on 2009-12-19
And first of all, why did you try to add it manually? Doing the update-grub can't find it and add it automatically?

---

### Post by darkod on 2009-12-19
[COLOR=Red]set root=(hd0,8 )
    search --no-floppy --fs-uuid --set 5ab69ff7-468c-4736-b535-e5416c2a6562
    linux    /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=693e59f9-9ad8-4f18-aed3-10ae0694499c ro   quiet splash
[/COLOR]
Is Fedora root partition your 8th partition?
Why are the UUIDs of boot and root partitions different? Do you have separate boot partition for Fedora? From my limited experience of Grub2 the UUIDs in both lines need to be the same, the root UUID, unless using separate boot partition.

---

### Post by v1nsai on 2009-12-20
Ah, didn't set the other UUID, that was it thanks.

Grub2 doesn't see the Fedora install, I don't know what the deal is.  I'm not liking Grub2 a lot :/

---

