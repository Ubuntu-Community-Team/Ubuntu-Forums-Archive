---
title: "Kernel panic when running a newly compiled kernel"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by madiyaan on 2010-07-10
Hello,

I have a Ubuntu 9.10 netbook edition and I am trying to compile a patched 2.6.32 kernel.

I copied over my current .config file and compiled the kernel.

When I try to boot into my shiny new kernel, I get this:

```

ACPI: Expecting a [Reference] package element, found type 0
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)

```

Does anyone know how to debug this problem?

**[EDIT]**: I selected from grub the recovery version of my compiled kernel, and it gave me this message:

```

VFS: Cannot open root device "sda1" or unknown-block(0,0)
Please append a correct "root=" boot option: here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0, 0)
Pid: 1, comm: swapper Not tainted 2.6.32perfctr #2
Call Trace:
...

```

Note: I have been following instructions from here how to compile this patched kernel. [http://debianclusters.org/index.php/Adding_Performance_Counters_to_the_Kernel](http://debianclusters.org/index.php/Adding_Performance_Counters_to_the_Kernel)

My goal is to use perfctr with 2.6.32 (I know PCL is available, but I want to use perfctr for my own reasons).


**[EDIT2]** Seems like in my grub2 menu.cfg, the difference between the working and non-working kernel is this:

The working kernel has (as the last line of menuentry):

```

initrd /boot/initrd.img-2.6.32-21-generic

```

while the non-working image does not have this line.

Note that I compiled the kernel using this command:

```

fakeroot make-kpkg --initrd --append-to-version=perfctr kernel-image kernel-headers

```

And I installed using this command:

```
sudo dpkg -i linux-image-2.6.32perfctr_2.6.32perfctr-10.00.Custom_i386.deb
```

Could this be the cause of the problem? Any ideas how to solve it?

---

