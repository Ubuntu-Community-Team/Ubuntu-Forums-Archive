---
title: "lvm root device does not exist"
date: 2017-05-02
forum: Installation &amp; Upgrades
---

### Post by Nigel_Pain on 2017-05-02
I've been upgrading a VM from 12.04 LTS to 14.04 LTS. All went well with the upgrade process but when I rebooted it dropped into initramfs with the message:

ALERT! /dev/mapper/root--vg-root does not exist. Dropping to a shell!

If I type "exit" it boots fine, but next time I reboot I get exactly the same problem. I'm fairly inexperienced with Linux so I don't really know what the cause is or how to resolve it. Suggestions gratefully received!

Thanks.

---

### Post by Nigel_Pain on 2017-05-03
Sorted. I found a similar issue on askubuntu.com. In /etc/default/grub, I changed:
GRUB_CMDLINE_LINUX="" to
GRUB_CMDLINE_LINUX="rootdelay=90"
and ran "update-grub"
issue is apparently that the rootdelay was set too low for 14.04. It's odd though because I've upgraded a couple of other VMs without problem.

---

