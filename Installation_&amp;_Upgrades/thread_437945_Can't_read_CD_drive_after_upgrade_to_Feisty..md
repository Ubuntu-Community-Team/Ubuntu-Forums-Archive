---
title: "Can't read CD drive after upgrade to Feisty."
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by greg9000 on 2007-05-09
I have an HP-epc42. I tried installing 7.04 from the CD but the boot failed with an ATA timeout. Instead I upgraded the existing 6.06 LTS installation to 7.04 (via 6.10). The system works but I can't access the CD drive.

I understand that with the new kernel all drives are now treated as SATA and should therefore show up in /dev as SCSI devices (how do you say "I curse your greasy beard" in Welsh?) and sure enough /dev/hda1 now seems to be /dev/sda1. But there's no /dev/scd0 nor /dev/cdrom.

If I reboot and select the 2.6.17-11 kernel installed with 6.10 /dev/hdc and /dev/cdrom (symlink to /dev/hdc) reappear and I can access the drive. 

From /var/log/syslog running 2.6.17-11 -

Probing IDE interface ide1...
May  9 23:02:01 XXXX kernel: [17179577.636000] hdc: SR243T, ATAPI CD/DVD-ROM drive
May  9 23:02:01 XXXX kernel: [17179578.308000] ide1 at 0x170-0x177,0x376 on irq 15

Since the new kernel doesn't recognize the CD drive it's not really surprising that booting from the 7.04 CD fails - the kernel can't mount the CD it was loaded from.

Apart from that I'd say 7.04 is Feistalicious. I've never felt so alive.

---

