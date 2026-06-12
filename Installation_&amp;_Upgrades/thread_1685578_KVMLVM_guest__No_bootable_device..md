---
title: "KVM/LVM guest:  No bootable device."
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2011-02-10
Hi,

I'm installing Ubuntu Server 10.10 as a KVM guest.  It has lvm2, and is installed as a kvm minimal guest.  I added ssh server and nothing else, and I formatted using lvm and guided mode, using 1G of the current allocation of a 10G /.

This is my first kvm attempt at all, so I don't know exactly what I'm doing.

I get to the reboot without the CDROM, and it tells me no bootable device.

I've launched from the installer in rescue mode, mounted /boot and rewrote grub.

Not sure what I'm doing wrong here.  Is it grub-related or KVM or just me?

Thanks in advance.

---

