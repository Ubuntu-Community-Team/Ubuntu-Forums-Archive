---
title: "&quot;Gave up waiting for root&quot; with LVM on LUKS"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by cookiecaper on 2013-03-02
Hello. I have a laptop here that has an LVM on LUKS setup. I had cause to regenerate the initramfs from a Live CD and chroot, and this apparently harmed the GRUB line that boots the system.

I now get a BusyBox shell on every boot after the kernel fails to open the root device. I can manually open the device from here with cryptsetup, exit the shell, and the boot continues happily. *After* I do this, I see a passphrase prompt but it's not necessary to fill out and doesn't take any input (presumably because the device is already unlocked).

I would really like this to work again without requiring the full cryptsetup command and BusyBox cycle. What is the standard GRUB line required?

Right now I have

```
linux /vmlinuz_something_something root=/dev/mapper/ubuntu-root ro verbose vga=z
```

I've tried lots of different things, including specifying a cryptdevice and a rootdelay. Would really like help on this.

It seems that anyone else who has had this problem has assumed their system was nuked and did a full reinstall. That sounds awfully extreme to me. I just need to know, based on Ubuntu's configuration, how do I do this? I can do it fine on Arch boxes, but Ubuntu seems to do things differently.

---

### Post by niXel on 2013-05-18
I have exactly the same problem now. Any news on this?

---

