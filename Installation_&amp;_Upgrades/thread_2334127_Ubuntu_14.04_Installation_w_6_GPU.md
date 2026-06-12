---
title: "Ubuntu 14.04 Installation w/ 6 GPU"
date: 2016-08-16
forum: Installation &amp; Upgrades
---

### Post by glambeth on 2016-08-16
Hi, I'm attempting to install ubuntu 14.04 with 6gpus. I have been running into problems the past 3 days and am not sure what else to do, so I figured I would come to the forums for help. I have a Gigabyte GA-Z10X-UD5 motherboard, an intel core i7-6700K 8M Skylake processor, and 6x AMD RX 380. I have vt-d enabled in the bios as well as XHCI. On boot I've tried various kernel parameters (iommu=soft, nomodeset, pci=nomsi, intel_iommu=on, etc) but nothing has worked. After setting the kernel parameters I just get a black screen with a litany of error messages:
```
[COLOR=#333333][FONT=monospace][ 1108.493365] pcieport 0000:00:03.0: AER: Corrected error received: id=0018[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace][ 1108.493378] pcieport 0000:00:03.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=0018(Receiver ID)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace][ 1108.493385] pcieport 0000:00:03.0: device [8086:d138] error status/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]mask=00000001/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]00001100[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace][ 1108.493391] pcieport 0000:00:03.0: [ 0] Receiver Error[/FONT][/COLOR]
```
that just continuously repeats. I've tried searching the forums but haven't had any luck yet, thanks!

---

### Post by gordintoronto on 2016-08-17
Is there a typo in your motherboard model? Google suggested GA-Z170X-UD5

However, when I look at the picture, it's not clear how one would install six video cards.

Have you considered trying a single video card?

Also, with the latest hardware, you should use the latest OS, not 14.04.

---

### Post by QIII on 2016-08-17
The fglrx driver cannot be used with 16.04, so multiple GPUs would be of limited use.  14.04 (but not 14.04.5) would be better in that regard.

But yes...  three PCI-e slots make 6 cards a bit difficult.

3 R9 295x cards would get you 6 GPUS on three PCI-e slots, but might dim all the lights in the house.

---

### Post by oldfred on 2016-08-17
Review of several AMD cards with 16.04:
[http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1](http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1)

But he often uses ppa to get even newer drivers & kernels.

---

### Post by glambeth on 2016-08-17
There is indeed a typo. That's the correct model. I just x1 -> x16 powered risers. Yup, works with a single video card. I haven't had problems in the past with 6 cards on ubuntu 14.04 while using AMD processors.

---

