---
title: "Please Advice : Dual Boot Windows 7 with Ubuntu 14.04 with TrueCrypt Installed"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by bngguy on 2014-04-19
Hello,
        I'm trying to install Ubuntu 14.04 on a laptop which already has Windows 7 Home Premium Installed and also the hard drive has been encryped with TrueCrypt, when i try to install Ubuntu 14.04 64bit it asks me for a mount point, see attached screenshots below, i would really appreciate if anybody could advise as to what mount point is to be selected.

Thanks,
bngguy

---

### Post by oldfred on 2014-04-21
You are showing the / (root) which is the very minimum required. Normally swap is also added.

But with truecrypt you may not want to install grub to MBR like most should.
But I do not know how truecrypt works.

One user just used a small flash drive and specified that as the location for the grub boot loader. You show it installing to sda8, but BIOS will not give an option to boot that.
Then when he wanted to boot Ubuntu he plugged in flash drive and choose that as boot device.

---

