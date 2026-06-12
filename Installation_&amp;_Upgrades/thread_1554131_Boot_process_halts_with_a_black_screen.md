---
title: "Boot process halts with a black screen"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by Jacobian on 2010-08-16
I'm trying to update an older laptop for my nephew. It was running Hardy Heron (Ubuntu 8.04 LTS) successfully.

However, after installing a clean copy of Lucid Lynx (Ubuntu 10.04 LTS), the boot process halts almost immediately with a black screen. There is no blinking cursor and no hard-drive activity.

When I hold down the "Shift" key after the rebooting the computer, I'm able to edit the grub2 boot options.

When I remove the "quiet" boot option, I'm able to see about a page of text before the boot process halts and displays the black screen. Here is the last bit of text that appears just before the black screen:

```
...
Begin: Running /scripts/init-bottom ...
Done.
```

At this point, the font style changes slightly. Then the text is replaced by the solid black screen. There is no blinking cursor, and the hard drive activity ceases.

I've tried booting in rescue mode: This also halts at a solid black screen.

This is an older laptop: I had to boot the installation disc with the boot option "noapic" in order for the installation disc to run.

However, the installation seemed to run normally. I was able to finish installing the system. But, after removing the installer disc and rebooting, we were met with that solid black screen almost immediately after booting.

I used the minimal install disc:
[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

I've verified the MD5 checksum for the disc image. And I've successfully used this same disc to install Ubuntu for my mother.

But my little nephew is left without a usable system.

Could we be missing a boot option?

Is there anything else you would suggest we try?

---

### Post by Jacobian on 2010-08-16
Okay, it turns out we needed the additional boot parameter: **nomodeset**

Here is some background information on the Kernel Modesetting feature:
[https://fedoraproject.org/wiki/Features/KernelModesetting]("https://fedoraproject.org/wiki/Features/KernelModesetting")
[http://wiki.debian.org/KernelModesetting]("http://wiki.debian.org/KernelModesetting")

This explains what Kernel Modesetting is, and why we needed to disable it.

---

