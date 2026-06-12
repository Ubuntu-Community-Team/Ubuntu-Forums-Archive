---
title: "Kernel 5.0.0 does not boot after upgrade to 19.04 (old kernel 4.18.0 works)"
date: 2019-06-01
forum: Installation &amp; Upgrades
---

### Post by lifesizejesus on 2019-06-01
I upgraded my Xubuntu 18.10 installation to 19.04 and my laptop won't boot anymore unless I choose the older kernel version. I tried Xubuntu 19.04 live USB and it works. I assume it uses 5.0.0 kernel by default.

I get a lot of ACPI related errors, so I tried passing acpi=off in kernel parameters. It got rid of the BIOS errors, but apart from those it looks the same:

[IMG]https://i.postimg.cc/NF25Lc3z/kernel5boot2.jpg[/IMG]

Apparently it can't find the root partition, but I don't think there's anything wrong with my partitions because the older kernel boots up just fine. Any ideas on what's going on here?

---

### Post by ubfan1 on 2019-06-02
Try booting the older kernel, and then run sudo update-grub.  That should ensure the UUID is used on the kernel boot line for root= xxx.  There was an old bug, which may be back, which used a device instead of the UUID,  If you save a copy of /boot/grub/grub.cfg before the update-grub, you can do a diff with the old and new versions to see if anything was changed.

---

### Post by lifesizejesus on 2019-06-03
I ran 'sudo update-grub', but it didn't make any changes to grub.cfg

---

### Post by lifesizejesus on 2019-06-03
Solved it! 

For some reason the upgrade had removed cryptsetup packages, so it couldn't see my encrypted LVM partitions. I booted up using the old kernel, reinstalled the cryptsetup package. At next boot it asked for the encryption password and booted up without problems!

---

