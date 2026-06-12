---
title: "Boot from external USB 3.0 harddisk"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by LoermansA on 2012-01-15
Hello all,

I've been scratching my head for a couple of days as to why I'm unable to get my laptop to boot from a WD Passport external harddisk connected via usb 3.

A little background info first. I've got a company laptop with Win7 on it and I'd like to use Linux alongside Win7 but leave the internal harddisk be. No partitiong, no grub, nothing. The laptop is an HP Elitebook 8760w. So I figured I'd install Ubuntu 11.10 to an external harddisk with grub installed to the external disk as well and select that disk in the boot options my laptops bios provides. Installation went fine, but I can only boot Ubuntu if it is not connected to one of the 2 usb 3 ports. Running it from any other usb port works (not always, sometimes I have to try a second time, but hey, fine by me).

The thing is, I can run the installer/live cd from a usb stick connected to a usb 3 port just fine. Could it be that the usb controller is falling back to usb 2 mode for this device?

So, with the disk connected to a usb 3 port I get the grub menu and after selecting Ubuntu Linux it appears to start booting, but after a while it drops me to a busybox prompt with the following message:
```

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/xxxxxxxxxxxxxxx
```

If I 'ls /dev' it appears that only the internal disk was found, but not the external. How can this be? I've gotten past the grub menu, gotten a started kernel with initramfs. All these are on the external disk. How can the kernel not see the disk itself?

I've added xhci_hcd and usb_storage to /etc/initramfs-tools/modules and regenerated my initramfs figuring it could be that the needed modules are not loaded in time. No help.

dmesg gives me some clues as to why the disk is not recognized:

```
xhci_hcd 0000:26:00.0: Timeout while waiting for a slot
```

And some other message (I forgot exactly what it said) about being unable to reserve or use slot 1 or slot 2 for this device.

I hope this makes sense. If anyone is able to help me, I'd be very grateful.

Regards,

Arjan

---

### Post by LoermansA on 2012-01-17
Not really solved, but I've decided to just shrink the windows partition and install Ubuntu alongside Windows.

New problem; the laptop rarely boot to a problem free desktop. More often than not the entire screen is shifted and wrapped to the right by about one thirds (even the terminals CTRL-ALT-F1 ... F6). But even then I do see the login prompt. But after entering my credentials I see the wallpaper, but nothing more.

The GPU is an ATI FirePro m5950. Does anybody know if this one is supported through the open source drivers? I believe it is based off of the x6000 GPU series.

---

