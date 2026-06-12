---
title: "Kernel Upgrade"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by Frogs Hair on 2010-07-08
This only a question . I am having an issue with the Hardware & Driver Jockey which I have filed a bug report on. One of the suggestions on  the thread  I posted on , was to upgrade the kernel  to the one currently being used in 10.10 Alpha . It seems logical that if that kernel was intended for Lucid it would be in use . I would like some opinions on this . Thanks !

---

### Post by snowpine on 2010-07-08
Lots of various Ubuntu kernels here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

They are .deb files, which means you can download one you want and then just double-click it to install. Choose the "linux-image" package that matches your architecture, for example if you have a 64-bit install you might choose linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb

2.6.32 is (and always will be) the officially supported kernel for Lucid. You are free to experiment with newer kernels if you desire, at your own risk. You can always fall back on your old kernel by selecting it from the GRUB menu.

---

### Post by Frogs Hair on 2010-07-08
I'm running 64x and not sure if a kernel upgrade is the answer to my issue. When the next normal kernel update comes wouldn't lucid just install a downgraded  kernel ?

---

### Post by snowpine on 2010-07-08
> **Frogs Hair said:**
> I'm running 64x and not sure if a kernel upgrade is the answer to my issue. When then the next normal kernel update comes wouldn't lucid just install a downgraded  kernel ?

Unless you have a specific reason for installing a different kernel, the default Lucid kernel (2.6.32) is your easiest and best-supported option. So long as you stay current with updates, you'll always have the latest bug fixes and patches.

---

### Post by Frogs Hair on 2010-07-08
> **snowpine said:**
> Unless you have a specific reason for installing a different kernel, the default Lucid kernel (2.6.32) is your easiest and best-supported option. So long as you stay current with updates, you'll always have the latest bug fixes and patches.

I see nothing in the latest kernel release notes to suggest a fix for my bug so I will stay with what I have . Thank You !

---

