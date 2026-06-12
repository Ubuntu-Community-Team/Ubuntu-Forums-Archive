---
title: "SATA2 Controllers not being Recognised by Ubuntu 7.04"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by Starcraftmazter on 2007-09-12
Hello thar.

I just purchased a PC with this motherboard:
**[http://www.gigabyte.co.za/Products/Motherboard/Products_Overview.aspx?ProductID=2407](http://www.gigabyte.co.za/Products/Motherboard/Products_Overview.aspx?ProductID=2407)**

Using this chipset:
**[http://www.via.com.tw/en/products/chipsets/p4-series/p4m900/](http://www.via.com.tw/en/products/chipsets/p4-series/p4m900/)**

The PC came with one 80GB SATA2 HD.
I also bought another 160GB SATA2 HD.

I have winblows on the 80GB HD. I wish to now install Ubuntu 7.04 on the 160GB HD. Unfortunately, Ubuntu cannot detect the VIA SATA controller.

Does anyone have any experience on how to deal with this?


Some information:
RAID will **not** be used.
If relevant, the 2nd (160GB) HD was installed after the windows install on the 80GB one.
Both HDs are detected by BIOS without apparent fault.
Windows detects 2nd HD, but does now show it as a disk (in GUI, eg. my computer), probably because it's not formatted.


_Thank you._

---

### Post by Pumalite on 2007-09-12
This might help (not sure):

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg421348.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg421348.html)

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg444758.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg444758.html)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/55346](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/55346)

---

### Post by Starcraftmazter on 2007-09-16
Ok, using via's sata driver installer, I've got Ubuntu installed and working on the 2.6.20-15 kernel.
Now I need to compile the drivers for the 2.6.20-16 kernel, but via's makefile doesn't seem to work.

I was wondering if anyone here whom writes Makefiles can have a look and see if it has a problem.

```
#begin
KERNVER = `uname -r`
KERNELDIR = /lib/modules/$(KERNVER)/build
obj-m := sata_via.o ahci.o
PWD := $(shell pwd)
all:
 $(MAKE) -C  $(KERNELDIR) SUBDIRS=$(PWD) modules
#end

```

The output is, "Nothing to do for all", and so the two .ko files don't get made.

The full guide is here, if anyone needs to check:
[http://www.viaarena.com/Driver/via_ubuntu7.04(x86&x86_64)_sata&ahci_patch_kernel_2-6-x_v1.30_appnote_ver0.8.tar.gz](http://www.viaarena.com/Driver/via_ubuntu7.04(x86&x86_64)_sata&ahci_patch_kernel_2-6-x_v1.30_appnote_ver0.8.tar.gz)
It's readme.doc, section 4


I've been posting about my problem on the via forums, but thus far nobody has replied about this specific issue.

---

### Post by Starcraftmazter on 2007-09-16
My friend pointed out to me that the space before $(MAKE) should be a tab, and the drivers compiled.

I copied them to the correct place,
/lib/modules/2.6.20-16-generic/kernel/drivers/ata
Yet the 20-16 kernel still won't start.

Any ideas?

---

### Post by Starcraftmazter on 2007-09-17
Issue Solved.

For reference, I took the installer with the 2.6.20-15 drivers, replaced the -15 drivers with the compiled -16 drivers, and modified the shell installer for the -16 kernel.

---

### Post by Pumalite on 2007-09-17
Use the 'Thread Tools' to mark it as Solved.

---

