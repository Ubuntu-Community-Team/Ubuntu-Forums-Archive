---
title: "Kernel panic: unable to mount root fs after building custom kernel"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by Bukran on 2010-02-17
Hello everyone.

I had to build a custom kernel (version 2.6.16) for development reasons. I downloaded the sources from [http://www.kernel.org](http://www.kernel.org) and compiled it with no major problem.

The thing is that, while booting, the system can't find /dev/sda1 and so a "kernel panic: unable to mount root fs on unknown-block (0,0)" appears on screen.

I'm running Ubuntu 9.10 (64 bits) with my custom kernel (2.6.16) over VMware. I know this sounds like a mess but it has to be done this way because several virtual machines are needed to be running at the same time.

Maybe I have forgotten some option in menuconfig that linux needs to boot in such a virtual drive. Any similar experience?

Thanks beforehand.

---

### Post by tom4everitt on 2010-02-17
You probably know a lot more than me, but I have a distinct memory of options directly related to virtual machines when compiling a kernel a while ago. Perhaps try activate all of them and recompile?

---

### Post by afrodeity on 2010-07-23
ALso have the same problem after installing latest kernel via kernelcheck

tried manually updating initramfs but it can't find the module. All the other kernels work no problem, just this one.

if I try to edit options on the grub menu I see it is not inited properly, just root=/sda1, my other kernels have proper init.

---

### Post by afrodeity on 2010-07-24
Contents of /boot showing a missing initrd.img for candela kernel

```

ls
abi-2.6.31-19-generic             memtest86+.bin
abi-2.6.31-20-generic             System.map-2.6.31-19-generic
abi-2.6.32-22-generic             System.map-2.6.31-20-generic
abi-2.6.32-23-generic             System.map-2.6.32-22-generic
abi-2.6.34-020634-generic         System.map-2.6.32-23-generic
config-2.6.31-19-generic          System.map-2.6.34-020634-generic
config-2.6.31-20-generic          System.map-2.6.34.1-candela
config-2.6.32-22-generic          vmcoreinfo-2.6.31-19-generic
config-2.6.32-23-generic          vmcoreinfo-2.6.31-20-generic
config-2.6.34-020634-generic      vmcoreinfo-2.6.32-22-generic
config-2.6.34.1-candela           vmcoreinfo-2.6.32-23-generic
grub                              vmlinuz-2.6.31-19-generic
initrd.img-2.6.31-19-generic      vmlinuz-2.6.31-20-generic
initrd.img-2.6.31-20-generic      vmlinuz-2.6.32-22-generic
initrd.img-2.6.32-22-generic      vmlinuz-2.6.32-23-generic
initrd.img-2.6.32-23-generic      vmlinuz-2.6.34-020634-generic
initrd.img-2.6.34-020634-generic  vmlinuz-2.6.34.1-candela

```

---

### Post by afrodeity on 2010-07-24
Solved the problem;

**Step 1**. cd /lib/modules

ls

This what my directory looks like:

```

/lib/modules$ ls
2.6.31-14-generic  2.6.31-20-generic  2.6.32-23-generic      2.6.34.1-candela
2.6.31-19-generic  2.6.32-22-generic  2.6.34-020634-generic

```

notice all the "modules" are named a certain way.

**Step 2**. man update-initramfs to see which options you need.

**Step 3.**
sudo update-initramfs <options> "module"
eg. sudo update-initramfs -c -k 2.6.34.1-candela

It should update and generate an initrd image

NOW this is an NB step

**Step 4.** sudo update-grub

---

### Post by fsm_apostle on 2010-08-11
> **afrodeity said:**
> Solved the problem;
...
**Step 3.**
sudo update-initramfs <options> "module"
eg. sudo update-initramfs -c -k 2.6.34.1-candela

It should update and generate an initrd image

NOW this is an NB step

**Step 4.** sudo update-grub

Thanks for that. I finally got my new kernel to not kernel panic. :)

---

### Post by afrodeity on 2010-08-11
Glad to be of assistance. I usually find with Ubuntu, whenever I have a problem, if I try to help others as well, the 'force" kicks in. :)

---

### Post by noletolucas on 2010-10-30
> **afrodeity said:**
> Solved the problem;

**Step 1**. cd /lib/modules

ls

This what my directory looks like:

```

/lib/modules$ ls
2.6.31-14-generic  2.6.31-20-generic  2.6.32-23-generic      2.6.34.1-candela
2.6.31-19-generic  2.6.32-22-generic  2.6.34-020634-generic

```

notice all the "modules" are named a certain way.

**Step 2**. man update-initramfs to see which options you need.

**Step 3.**
sudo update-initramfs <options> "module"
eg. sudo update-initramfs -c -k 2.6.34.1-candela

It should update and generate an initrd image

NOW this is an NB step

**Step 4.** sudo update-grub

Didn't work for me.

I was very happy to see that my system also missed one _initrd.img_, so I followed your steps, but it didn't work. The new img is know there, but the problem persists.

I'm running Ubuntu 10.04 on VirtualBox virtual machine, compiled, build kernel linux-2.6.32.25 and modules. :(

But thanks anyways.

---

