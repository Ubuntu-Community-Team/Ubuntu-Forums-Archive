---
title: "Grub disappeared in dual boot Windows/Ubuntu after BIOS reset to default"
date: 2022-03-06
forum: Installation &amp; Upgrades
---

### Post by martin-gander on 2022-03-06
Hi,

I unfortunately did a BIOS reset to default in my dual boot Ubuntu/Windows Thinkpad Yoga yesterday, and when booting again, it only boots into Windows, which I have never used, I dont get to grub any more where I could choose ubuntu normally. I found the boot-repair tool, and when using it from a live usb ubuntu from which I had installed ubuntu 2 years ago, I can use it, but it hangs when choosing Recommended Repair. I generated the BootInfoSummary which should be available here

[https://paste.ubuntu.com/p/wWYj2r5t7r/](https://paste.ubuntu.com/p/wWYj2r5t7r/)

Can anybody see why boot-repair gets stuck and does not finish (I left it running for more than an hour)

Many thanks in advance

Martin Gander

---

### Post by grahammechanical on 2022-03-06
Re-setting the UEFI/BIOS has not removed the boot files in the EFI System Partition (nvme0n1p1) but is has changed the boot priority order. Enter the UEFI settings utility and set the boot order to /efi/ubuntu/shimx64.efi as suggested by the Boot Repair summary report.

If Ubuntu loads open a terminal and run

```
sudo update-grub
```

and see if it still lists Windows as it should. As another option you might need to set the boot priority to /efi/ubuntu/grub.cfg in order to see a Grub boot menu when you load.

Regards

---

### Post by oldfred on 2022-03-06
You show UEFI Secure Boot on.
Did you install Ubuntu with Secure Boot on? 
Shimx64.ef/grub does not boot Windows with Secure boot on. Something about chain of security. But you should be able to boot from UEFI boot menu.
UEFI updates often reset some UEFI settings back to defaults. I have to keep a list as multiple settings change.

And Windows (or grub) updates reset system so that system is first in UEFI boot order. You just have to boot from UEFI boot menu and reset boot order using efibootmgr or in UEFI settings, you should be able to change boot order.

---

