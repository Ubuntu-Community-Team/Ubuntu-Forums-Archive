---
title: "will a MBR type boot capable USB stick with Mate 18.04 work with a GPT system?"
date: 2019-12-14
forum: Installation &amp; Upgrades
---

### Post by james2b on 2019-12-14
So will a MBR type boot capable USB stick with Mate 18.04 on it work with a GPT and UEFI system? I create it with my Windows 7 older system with MBR and BIOS, and then plug it into my newer Windows 10 system which has both the GPT and UEFI and try to boot it up?

---

### Post by mikewhatever on 2019-12-14
It should, because Ubuntu images are hybrid, and work well with UEFI and BIOS only systems. It is irrelevant what system the USB stick was written on.

---

### Post by james2b on 2019-12-14
Okay thanks, and so then which partition method type is best to use on a USB flash drive so that it is reliable and durable, MBR or the newer GPT type? It is a 32 GB newer stick, and using the Rufus USB creator utility tool as suggested in the Ubuntu tutorial.

---

### Post by mikewhatever on 2019-12-14
I don't know which method is the best or second best..., and it doesn't matter. A USB drive is "reliable and durable" if it's been manufactured properly at a factory of origin. How it is partitioned is also irrelevant because Rufus will overwrite it anyway.

---

### Post by james2b on 2019-12-14
So with it formatted by the Rufus tool as MBR, will it get detected okay and be able to boot into the Ubuntu Mate 18.04 when connected to the newer UEFI computer? I thought that GPT is required for a system booting with UEFI? Maybe that rule only applies to the internal drives, so not to external portable devices?

---

### Post by mikewhatever on 2019-12-14
Pretty sure it can be both, but MBR works just fine, as indicated by this screenshot: 

[IMG]https://tutorials.ubuntu.com/es6-bundled/src/codelabs/tutorial-create-a-usb-stick-on-windows/img/2a7ef863cd5ea8c.png[/IMG]

Bootable USB howto reference: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#5](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#5)

---

### Post by yancek on 2019-12-14
> I thought that GPT is required for a system booting with UEFI?  

A UEFI install is NECESSARY on a GPT disk ONLY for windows.  It is not necessary for Ubuntu or any Linux OS as it is possible to create a BIOS_boot partition on the GPT drive and install Ubuntu/Linux in Legacy mode using the MBR.

It's the iso you use to create the bootable usb that is important.  The link below to the Ubuntu documentation explains how to tell if you are booting in EFI mode.  Simplest way to ensure that is to disable Legacy/CSM in the BIOS.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by sudodus on 2019-12-14
Please notice that cloning is the simplest method to create a USB boot drive. It means that you copy every bite from the iso file to the target drive without any modification. See this link,

[help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

All current Ubuntu iso files make USB drives, that can boot both in UEFI mode and BIOS (legacy) mode (except the mini.iso files, that make USB drives that can boot only in BIOS mode).

---

