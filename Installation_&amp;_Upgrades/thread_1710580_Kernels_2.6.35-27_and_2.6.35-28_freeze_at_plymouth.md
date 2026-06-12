---
title: "Kernels 2.6.35-27 and 2.6.35-28 freeze at plymouth boot splashscreen"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by gluonman on 2011-03-20
Hello Ubuntu community,

I am running 64-bit Ubuntu 10.10.  I have installed burg, which is an alternative to grub, and an alternative plymouth boot splash as well.  This setup has been working fine for me, except that after using gimp to edit the logo.png image from the plymouth boot splash recently, and then running 'sudo update-initramfs -u && sudo update-burg' (this while using kernel 2.6.35-27), the kernel will no longer get passed the plymouth boot splash.  The boot splash appears to work fine, and even reflects the change I made to the logo, but then it freezes.  I installed kernel 2.6.35-28 and it suffers the same problem.  I am limited to using kernel 2.6.35-25, which still loads fine and does not reflect the change I made to the logo.

I have been having a hard time identifying the source of the problem.  The only time I've messed with the kernel lately is when I was getting my android phone to mount when connected via USB.  I used the following commands when following suggestions online:

1.  sudo rmmod ehci_hcd (before I realized that this module is now built-in to the kernel)

2.  sudo rmmod ohci_hcd

3.  sudo sh -c 'echo -n "0000:00:12.2" > /sys/bus/pci/drivers/ehci_hcd/unbind' && sudo sh -c 'echo -n "0000:00:13.2" > /sys/bus/pci/drivers/ehci_hcd/unbind'

4.  sudo sh -c 'echo -n "0000:00:12.2" > /sys/bus/pci/drivers/ehci_hcd/bind' && sudo sh -c 'echo -n "0000:00:13.2" > /sys/bus/pci/drivers/ehci_hcd/bind' (did this one by accident the next time the android failed to mount -- I intended unbind)

Might the above have had something to do with why my kernels are broken now?

Other than that, I'm a bit lost.  I'm not sure how to identify this issue or how to fix it.  Any information that I should provide that would be helpful for you to help me, please let me know.  I look forward to your responses.

Cheers!

---

