---
title: "Add kernel modules to initrd.gz"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by CBruyland on 2010-10-27
I'm in the process of automating the installation of Lucid on our Hyper-V guest machines.
The Hyper-V guest components kernel modules are not available in the initrd.gz, 

I extracted the initrd.gz using:
```
gunzip -dc ../initrd.gz | cpio -imvd --no-absolute-filenames
```Downloaded the full kernel package (linux-image-2.6.32-25-generic_2.6.32-25.45_amd64.deb), extracted the Hyper-V modules (hv_vmbus.ko, hv_storvsc.ko, hv_netvsc.ko and hv_blkvsc.ko).

I copied these files to the extracted initrd.gz:
```
/lib/modules/2.6.32-25-generic/kernel/drivers/staging/hv/
```and I recreated the initrd.gz using:
```
find . | cpio -o -H newc | gzip > ../initrd.gz
```Now when I boot using the custom initrd.gz, and change to another console, I can  load these modules by hand; and the synthetic components are detected.

How can I change this, so these additional modules will be loaded during booting?

---

### Post by superpriz on 2010-11-25
Hello, i'm not sure but i think that you should add "insmod" command to init script that in initrd.img. In you case you've just added kernel module to RAM disk but nobody had loaded it. As i wrote above - add loading of your module into kernel in init script.
If my description is bad look here [http://www.microsuncn.com/index.php?title=Analysis_linux_initrd](http://www.microsuncn.com/index.php?title=Analysis_linux_initrd), may be you'll understand what i meant.

Please, answer if it was solving of problem.

---

