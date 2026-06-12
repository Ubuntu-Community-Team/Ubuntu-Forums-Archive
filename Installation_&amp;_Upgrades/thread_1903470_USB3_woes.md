---
title: "USB3 woes"
date: 2012-01-02
forum: Installation &amp; Upgrades
---

### Post by lucisandor on 2012-01-02
Hi all,
I am trying to hook a Mediasonic H82-SU3S2 (USB3 enclosure which can hold 8 SATA drives) to a Rosewill RC-505 PCIe-to-USB3 adapter. It works surprisingly well in 11.04 and even some earlier versions of Ubuntu, with automount. But in 11.10 they do not mount even manually. I can see the drives in /proc/partitions, but the syslog is flooded with
```
Jan  2 02:43:32 battlecruiser kernel: [  551.160769] usb 3-1: reset SuperSpeed USB device using xhci_hcd and address 4
Jan  2 02:43:32 battlecruiser udevd[3693]: '/sbin/blkid -o udev -p /dev/sdo' [7632] terminated by signal 9 (Killed)
Jan  2 02:43:32 battlecruiser udevd[3695]: '/sbin/blkid -o udev -p /dev/sdk5' [4667] terminated by signal 9 (Killed)
Jan  2 02:43:32 battlecruiser udevd[3693]: timeout 'udisks-part-id /dev/sdo'
Jan  2 02:43:32 battlecruiser udevd[3695]: timeout 'udisks-part-id /dev/sdk5'
Jan  2 02:43:32 battlecruiser kernel: [  551.181469] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Jan  2 02:43:32 battlecruiser kernel: [  551.181599] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801af985880
Jan  2 02:43:32 battlecruiser kernel: [  551.181601] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801af9858c0
Jan  2 02:43:32 battlecruiser kernel: [  551.183311] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
Jan  2 02:43:32 battlecruiser udevd[949]: timeout: killing '/sbin/blkid -o udev -p /dev/sdl1' [7657]
Jan  2 02:43:32 battlecruiser udevd[948]: timeout: killing '/sbin/blkid -o udev -p /dev/sdi1' [7645]
Jan  2 02:43:33 battlecruiser udevd[3693]: timeout: killing 'udisks-part-id /dev/sdo' [7678]
Jan  2 02:43:33 battlecruiser udevd[3695]: timeout: killing 'udisks-part-id /dev/sdk5' [7679]
```The enclosure still works in 11.10 if hooked to a USB 2 port.
I think it is a bug, and I would file it as such, but I would like to make sure: did I miss anything? Do I have to do anything special to get USB3 working in 11.10?

---

### Post by cvolk on 2012-01-06
I am experiencing the exact same issue, same enclosure, but different controller: it's a Etron EJ168A running on an ASRock 970 Extreme3 with AMD 970/SB950 chipsets.  These messages appear even when the drive is quiet, and stall transfers when listening to music from a (dm)raid 5 array running on the drives in this enclosure.

I'm running the absolute latest kernel/packages as of today.

I will try to update here if I find a solution.

---

### Post by sdellutri on 2012-04-28
I am experiencing similar issue.  I have the same 8 bay enclosure which works great under Windows, but does not work properly with Ubuntu.
If I connect the enclosure to a USB2 port with Ubuntu it works perfectly, but of course limited to USB2 speeds.
I just upgraded to 12.04 LTS, but its still not working.
Does anyone have some suggestions?
thanks!

---

