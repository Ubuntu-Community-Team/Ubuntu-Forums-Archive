---
title: "Upgrading kernel to i686 on 6.10"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by benbooth on 2007-03-21
Hi
I recently bought a USB WiFi adapter which said is was supported by linux, but it turns out the chipset used IS supported from Kernel 2.6.18 onwards.
I currently run Kernel 2.6.17-11 which was installed during a system update.

Is there a way of using synaptic (or apt-get) to install a newer kernel image? and if possible a i686 kernel image?

Thanks,

Ben Booth

---

### Post by nim278 on 2007-03-22
You could try downloading the Feisty Fawn 7.10 testing .DEB from packages.ubuntu.com. However, it may cause problems with other packages or require you to upgrade them as well. I recall having a similar problem once and I ended up having to upgrade my whole system to get it to work.. but Feisty is still in alpha testing (though it has worked flawlessly for me for quite some time). You have to decide if a newer kernel is worth a few risks of having an alpha distribution.

You could also compile the kernel yourself from source, though this is a slightly more complicated process. There are some instructions here: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Good luck!

Maciek

---

