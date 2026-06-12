---
title: "Problem with Dapper Upgrade to Kernel 2.6.15-26-386"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by hbradlow on 2006-08-12
I am running Ubuntu Dapper under VMWare Player (as a guest). It was working well until I recently upgraded from kernel 2.6.15-25-386 to kernel 2.6.15-26-386. After the upgrade, Ubuntu failed to recognise my network connection which had previously been working. If I check the network using Ethereal, it fails to recognise that I have a network card installed.

The only workaround I have found is to interrupt the GRUB boot process and to  boot using the previous kernel (2.6.15-25-386). As a relative newcomer to Unix I have not found a way of modifying the menu.lst file to make it automatically boot with the previous kernel (I did change the menu.lst file, but the system would not boot when I commented out the lines for kernel 2.6.15-26-386). 

I would be grateful for any help:
1. Any ideas why my network fails to be recognised under kernel 2.6.15-26-386?
2. Can someone point me to a reference which explains how to remove the kernel upgrade?

Thanks in anticipation.
Hugh

---

### Post by hbradlow on 2006-08-14
Sorry - I solved my own problem. I was using the vmxnet network device with Vmware Player and you need to reconfigure the vmware tools with the new kernel for it to work. The alternative is to switch the network device to e1000.

---

