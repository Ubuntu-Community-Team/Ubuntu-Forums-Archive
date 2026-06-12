---
title: "Computer doesn't recognize hard drive after ubuntu install"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by trotur on 2010-11-01
Hi!

I'm having really strange problems after ubuntu 10.04.1 i386 server install. Installation runs well and grub becomes installed. In first boot computer doesn't anymore recognize hard drives at all.

In the boot procedure computer seems to 1) check ram, 2) check ide/sata devices and 3) boot from some device. Computer isn't able to recognize my hard drives in step 2). System just does nothing: doesn't print any errors and doesn't become unresponsive. I can press F2 and there will appear text "Entering BIOS", but bios is never accessed because boot procedure fails before bios setup is opened. Thus I also can't boot using live-cd.

If I disconnect hard drive, I can enter bios setup normally. Moreover if I plug drive to some other computer, I can boot normally from this drive. Further I can format drive using this working system and then drive will work again in the first system.

I have noted that boot fails when SATA hard drive is connected to controller:
1) SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
or
2) some old IDE-emulating SATA-controller from Intel (also IDE-drives fails with this controller). I can find out exact model of this controller if it is necessary.

In the motherboard that has SATA-controller 1), there is also controller:
SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02).
I can boot hard drive with no problems when it is connected to this controller.

I don't think that those not-working controllers would be broken since I can install ubuntu using them but they just doesn't recognize the drive with ubuntu installed.

I have also installed ubuntu 10.10 amd64 desktop and problems are exactly same as with ubuntu 10.04.1 i386 server. I think that ubuntu 10.04 (not 10.04.1) was last version working, but I can't confirm that since 10.04.1 seems to have totally replaced 10.04.

I would appreciate any comments about how to try to fix this problem.

---

