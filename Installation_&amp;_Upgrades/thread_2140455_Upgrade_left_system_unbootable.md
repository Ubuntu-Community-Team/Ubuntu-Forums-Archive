---
title: "Upgrade left system unbootable"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by arathorn2nd on 2013-04-29
Hello guys,

Just upgraded from quantal using update manager. Upgrade was successfull but left system unbootable.
Trying to boot on recovery mode I see the system hangs on **Trying to unpack rootfs image as initramfs...**
Tried the leftover kernels, same thing happens. Also tried fresh install on differente partition, same results.
I'm now stuck in LiveCD, which runs fine being 13.04.
I can chroot to the old system, tried installing 3.2 kernels, still no boot, hangs after **Begin: Running /scripts/init-bottom ... Done**

Anyone able to shed some light here? Already lost two hours trying to get my system back.

$ lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0040] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0042] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:16.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller [8086:3b66] (rev 06)
00:16.3 Serial controller [0700]: Intel Corporation 5 Series/3400 Series Chipset KT Controller [8086:3b67] (rev 06)
00:19.0 Ethernet controller [0200]: Intel Corporation 82578DC Gigabit Network Connection [8086:10f0] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b06] (rev 06)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c61] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
```

---

### Post by arathorn2nd on 2013-04-30
Ok, started diving in this cryptic mess.

Did a fresh install, got it running fine until I installed virtualbox and qemu-kvm. System unbootable after reboot.

While using chroot to remove the packages, the system locks when it gets to **update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic**
Running the update manually with verbose I see the issue is **Building cpio /boot/initrd.img-3.2.0-40-generic.new initramfs**
I can see a stalled cpio process consuming no cpu resources.

It seems a bug related to rebuilding the initrd after modules are added.
Still trying to get my system back, thou.

---

