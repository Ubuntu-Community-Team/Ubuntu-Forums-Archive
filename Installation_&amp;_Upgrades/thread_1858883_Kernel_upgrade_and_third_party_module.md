---
title: "Kernel upgrade and third party module"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by natarajmb on 2011-10-13
Hi All,

  Hope, someone with more understanding can help me here. I have a ubuntu server running on RocketRaid 2720 with RAID5. During installation I inserted the pre-compiled  raid card kernel module and finished the installation. All is fine so far.

  Say down the line I get a new kernel (which eventually have to happen)  I need to have my kernel module for raid card be recompiled using new kernel headers and be placed in newer kernel module directory and new initramfs be generated before I reboot into new kernel.  My question is how all this would happend i.e. Any pointer on how to compile a kernel module using different kernel headers than the currently running kernel. I searched in raid card documentation, it only talks about the current/running kernel. I am looking for pointers not necessarily to fit my case.

---

### Post by natarajmb on 2011-10-13
Okie found the solution, if anyone is looking for how to do it here is the pseudo steps.

1. Install you kernel image
2. Install respective kernel header package.
3. Compile your third party module using the new kernel header files. (For the card I am using it comes with driver with source along with compiling options passing the kernel dir to use to build the code)
4. Copy the built .ko module to correct folder (in my case i had to copy to /lib/modules/<new kernel dir>/kernel/drivers/scsi)
5. run "depmod -a <new kernel version>"
6. run "mkinitramfs -o /boot/initrd.img-<new kernel version> <new kernel version>"
7 restart and select the new version of kernel to boot.

---

