---
title: "Booting 2.6.16 in SATA drive"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by Mihelog on 2006-09-15
Hello everyone,
             I have installed ubuntu 6.06 on a Thinkpad T43, and I want to install the software for all it's features so I can use it instead of windows. I have installed all major features, such as fingerprint reader but I have stumbled upon HDD shock protection. I have downloaded kernel 2.6.16.28 and applied the queuefreeze patch in it's sources cleanly. I copied the config file from the existing kernel and tweaked it as the 2.6.16. kernel recompile thread says. I also enabled some features instead of leaving them as modules. I also enabled SCSI.
   The problem is that the new kernel cannot boot. After compiling and installing the generated .deb file, I go ahead to create the initrd image. In that process I get the errors:

/usr/sbin/mkinitrd: add_modules_dep_2_5: modprobe failed
FATAL: Module sg not found.
FATAL: Module sd_mod not found.
WARNING: This failure MAY indicate that your kernel will not boot!
but it can also be triggered by needed modules being compiled into
the kernel.

I couldn't easily locate which modules it refers to. If i try to boot from the kernel anyway, it fails because it tries to find and read "hda", instead of "sda". Unfortunately I can't exactly remember the error messages, If you need them I will paste them, but they were many error messages to read from "hda".

I would really appreciate any help. I don't want to use windows anymore, but I have lost so much time with the kernel thing. I think the queuefreeze patch didn't apply cleanly to 2.6.17 which is why i chose 2.6.16. I also tried applying the ultrabay hotswap patch, but that didn't apply cleanly either.

Thank you in advance,
    George M

---

