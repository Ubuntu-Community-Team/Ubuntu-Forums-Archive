---
title: "Update 4.15 kernel to 5.3 on 18.04 LTS"
date: 2019-12-20
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2019-12-20
The computer has Xubuntu 18.04 LTS, up to date. However, it is installed on a Thinkpad P73 (which I love!), which comes with the Intel® AX200 Wi-Fi 6 802.11AX (2 x 2) & Bluetooth® 5.0. I don't care about Bluetooth, but I frequently need wifi, and the wireless driver is not available until the 5.2 kernel. I found several web pages which purport to provide ways to install the driver on older kernels, but they all failed. I don't think I'm going to get the wifi on this computer working until I get the 5.3 kernel.

I could do a dist-upgrade to 19.10, but that's three dist-upgrades. I'm a big fan of dist-upgrades, but three is too much. I could wait until April and then do a dist-upgrade, which I plan to do anyway, but that leaves me without wifi for the next five months.

In Synaptic I find a number of packages with 'linux-' and '5.3,' and if I could do the upgrade just by installing packages that would be easy. Even a dummy like me could do that. But figuring out which packages to install is beyond me. And I don't even know if it is possible to install 5.3 on 18.04.

So is it possible? And if so, how? Is there a 'for dummies' guide?

---

### Post by CatKiller on 2019-12-20
> **John Jason Jordan said:**
> And I don't even know if it is possible to install 5.3 on 18.04.

It is.

The LTS releases have something called the Hardware Enablement Stack (HWE), which includes a new kernel, new xorg, and new Mesa from the later interim releases. 18.04.2 installs onwards automatically put users onto the HWE stack. Since you're on 4.15 that means that you installed an 18.04 image from before the 18.04.2 point release. If you were to install the HWE stack (which you'd be on anyway if you'd installed after 18.04.2) that would put you onto the 5.0 kernel branch.

As part of the HWE release process, the next release also needs testing so that it will be ready for HWE users. The next version of the kernel is the 5.3 that's in 19.10. This testing stack is called HWE-edge. Installing the HWE-edge stack will get you onto the 5.3 branch on 18.04. That will then get bumped up to the 5.5 branch around the time 20.04 is released, and then the normal HWE branch will go to 5.3.

If you're only after the kernel, and you're using -generic, the package you'd be after would be **linux-generic-hwe-18.04-edge**. Substitute the generic part if you're using -lowlatency or other kernel type.

---

### Post by John Jason Jordan on 2019-12-20
> **CatKiller said:**
> If you're only after the kernel, and you're using -generic, the package you'd be after would be **linux-generic-hwe-18.04-edge**. Substitute the generic part if you're using -lowlatency or other kernel type.

Perfect. I installed it, rebooted, and here I am:
uname -a
Linux Devil-Bonobo 5.3.0-24-generic #26~18.04.2-Ubuntu SMP Tue Nov 26 12:34:22 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

And the wifi is now working. Yay!

Thanks for the help!

---

### Post by mörgæs on 2019-12-21
Good, please mark the thread solved.

---

### Post by Impavidus on 2019-12-21
> **CatKiller said:**
> That will then get bumped up to the 5.5 branch around the time 20.04 is released, and then the normal HWE branch will go to 5.3.

If I'm not mistaken, the normal HWE branch will get to kernel 5.3 when support for kernel 5.0 gets dropped as Ubuntu 19.04 reaches end of life. This will happen in January. Around the same time the Ubuntu 18.04.4 live disk will be released, which will use the 5.3 kernel.

---

