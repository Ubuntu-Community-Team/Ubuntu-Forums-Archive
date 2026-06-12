---
title: "Grub setup for drive configured for EFI from non-EFI Bios"
date: 2016-10-08
forum: Installation &amp; Upgrades
---

### Post by macho3 on 2016-10-08
My hard drive no longer boots after I moved it into  an older laptop, which I believe is because the  BIOS doesn't support EFI. What's the simplest way to get  this to work? I've never been  good with grub/MBR/boot related issues.

The drive is set up like this:
/dev/sda1 has an EFI/ubuntu folder with grub.cfg, grubx64.efi, etc.
/dev/sda2 has a normal root partition setup with bin, boot, home, etc.
/dev/sda has nothing in its boot sector (hence the laptop just shows a blank screen + blinking cursor when I try to boot from it)

The laptop is a Thinkpad SL400c with American Megatrends BIOS version 6AET64WW (1.30), which seems to be the newest possible according to Lenovo's site. If it includes a way to enable EFI, I'm not seeing it.

I tried running the boot-repair utility, but it  refuses to do anything unless EFI is enabled.

Do I have to overwrite the contents of /dev/sda1 with something else? If so, how? If not, can I just reinstall a boot record on /dev/sda? How does that work?

Grateful for any help you can provide!

---

### Post by sudodus on 2016-10-08
It is possible to create boot drives that work in both BIOS and UEFI mode. What you need is a BIOS bootloader. 

Boot the computer from a DVD disk or USB drive with a live system of the same version as your installed system. Then you can install the (BIOS) bootloader according to the following link,

[Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by ubfan1 on 2016-10-08
If your disk partitioning is gpt instead of MSDOS, you will need another tiny partition (1-2Meg) with the grub-bios flag to allow the grub install to work.

---

### Post by macho3 on 2016-10-08
Great, thanks! When I set sda as the target bootloader device, sda2 as / and sda3 as swap and press "install now", it warns me that it's going to delete all system files "/etc, /lib, /usr, /var ...)" presumably to reinstall. Is there any way to avoid this and just have it write the bootloader on sda? I'm  keen to avoid touching the contents of the drive.

---

### Post by macho3 on 2016-10-08
Ok, I was able to get it to work thanks to your help doing the following:

1) In GParted:
  a) I shrunk my sda1 fat32 boot partition to 412MB
  b) I  created a new 100MB sda4 ext4 partition right before it, enabling the bios_grub flag
2) sudo mount /dev/sda2 /mnt
3) grub-install --boot-directory=/mnt/boot /dev/sda


Thanks again for the help! Very appreciated

---

