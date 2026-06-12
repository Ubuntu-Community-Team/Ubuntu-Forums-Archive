---
title: "Recompiling the Kernel (Feisty)"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by forfree on 2007-04-02
Ok, perhaps one of you guys can tell me where I'm going wrong here.

First off, the kernel in question is kernel version 2.6.20.4, which I got from:
[http://www.kernel.org/](http://www.kernel.org/)

I followed the directions from this site to recompile the kernel:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Everything went smoothly, started the reboot.  Got a "Kernel panic - not syncing VFS: Unable to mount root fs on unknown-block(0,0)" msg, so I booted back into kernel version 2.6.20-13-386, and ran:
```
$ sudo update-initramfs -u
Password:
update-initramfs: Generating /boot/initrd.img-2.6.20.4-custom
find: /lib/firmware/2.6.20.4-custom: No such file or directory
find: /lib/firmware/2.6.20.4-custom: No such file or directory
find: /lib/firmware/2.6.20.4-custom: No such file or directory
find: /lib/firmware/2.6.20.4-custom: No such file or directory
find: /lib/firmware/2.6.20.4-custom: No such file or directory
find: /lib/firmware/2.6.20.4-custom: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.

```

Even though it doesn't look like it succeeded I went ahead and rebooted to try again.  No Kernel Panic this time, but the xserver can't start.  Anyone have a clue what the next step I need to take is?

---

### Post by forfree on 2007-04-02
No one knows what's going on?

---

### Post by davidsch on 2007-04-02
I don't know what is happening here, but I am looking to recompile the kernel myself.  But rather than get the latest from kernel.org I was going to start with the ubuntu-supplied kernel source and include the various debug options I want.

I imagine this might be a safer path, but of course it doesn't help if you want the absolute latest kernel.

David

---

