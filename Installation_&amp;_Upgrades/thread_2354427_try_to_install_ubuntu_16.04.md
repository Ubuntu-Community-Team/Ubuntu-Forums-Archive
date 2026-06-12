---
title: "try to install ubuntu 16.04"
date: 2017-03-02
forum: Installation &amp; Upgrades
---

### Post by konec2 on 2017-03-02
Hi, 

I tried to install ubuntu 16.04 {64 bit version} on new laptop from USB live, but it always fails while ''installing grub2'' the pc freezes. I tried to install boot repair and this is what I got [http://paste2.org/CyIK6U9k](http://paste2.org/CyIK6U9k) 

Can anyone help me please?

Thank you.

---

### Post by oldfred on 2017-03-02
Did you run the suggested fixes by Boot-Repair. Or install to ESP - efi system partition on sda.

What brand/model system?

You have UEFI system with Secure boot on. Have you tried with secure boot off in UEFI?

Somehow you installed grub legacy into MBR. Do not attempt to boot in legacy/CSM/BIOS boot mode, that version of grub has not been used by Ubuntu since about version 9.10 although still in repository for some very old systems.

---

