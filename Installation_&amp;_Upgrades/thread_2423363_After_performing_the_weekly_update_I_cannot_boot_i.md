---
title: "After performing the weekly update I cannot boot into Ubuntu"
date: 2019-07-22
forum: Installation &amp; Upgrades
---

### Post by bpaulalex on 2019-07-22
Hello,

I do not have dual boot or anything, I did not perform anything out of the ordinary, just plain weekly usage, but:

- last week, on the 16th or 17th I just allowed the weekly updates to go through

I kept using the laptop, putting it in sleep, until I rebooted it this weekend.

When it tries to boot now, I get the following error:

```

error: /boot/vmlinuz-5.0.0.21-generic has invalid signature
error: you need to load the kernel first.

Press any key to continue...

```

If I use the boot Advanced options and boot using 5.0.0.20, everything is perfectly normal and functions without any issues.

I updated from this version using apt-get update and upgrade, tried to reboot, and the issue persists.

Any ideas?

If necessary, I can try and get a Boot-info log, but I was wondering whether i should get that log when booting with 5.0.0.20 or I need to create a USB stick which has either Ubuntu live or Boot-repair on it.

Thanks!

---

### Post by Artim on 2019-07-22
Grub (the bootloader) needs to be updated to include the new kernel you just got.

---

### Post by bpaulalex on 2019-07-23
Tried this:

```
sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.0.0-21-generic
Found initrd image: /boot/initrd.img-5.0.0-21-generic
Found linux image: /boot/vmlinuz-5.0.0-20-generic
Found initrd image: /boot/initrd.img-5.0.0-20-generic
Adding boot menu entry for EFI firmware configuration
done




```

Problem persists. I can only boot into 5.0.0.20

---

### Post by bpaulalex on 2019-07-25
Anyone, any ideas please?

---

