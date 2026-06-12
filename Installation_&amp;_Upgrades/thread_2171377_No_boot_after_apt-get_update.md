---
title: "No boot after apt-get update"
date: 2013-08-30
forum: Installation &amp; Upgrades
---

### Post by wykat on 2013-08-30
Hi,

I'm using a KVM server for about a year and after an apt-get update (12.04) and reboot it doesn't start anymore.

I've used boot-repair but this doesn't help. It looks like the apt-get update changed the system from a legacy system to efi (SDA1 EFI, SDA2 /boot, SDA3 /), so there is no BIOS_grub partition. Nevertheless the BIOS doesn't see a UEFI HDD, only USB (MB ASUS E35M1 deluxe)

When I run boot-repair it asks me to perform some manual tasks (e.g. dpkg --configure -a, purge grub*-common and install grub-efi). It also asks for raid drivers, but after the problems started I've removed the data disks (MD0), the boot disk is a non-raid disk. The strange things are with [ -d /mnt/sda3/sys/firmware/efi ] && echo "efi" || echo "legacy" I get following behavior:
before boot-repair: legacy
After manual entries: efi
After completing boot-repair: legacy

When I interrupt boot-repair after manual entry it remains efi, but after reboot the system still only boots from USB stick and the HDD (samsung SSD 840 pro) goes back to legacy. Also the BIOS doesn't show the SSD as UEFI option after the reboot

in paste.ubuntu.com I have following entries:
after copying original SSD to new Samsung SSD: 6044022
after completing boot-repair: 6044246
after interruption of boot-repair and before reboot: 6044315
after reboot: 644330

I also had to reinstall the MBR which had disappeared from both the original and copied SSD (shown in 6044022).

any idea's/proposals to get this system working ??

rgrds,
Andy

---

