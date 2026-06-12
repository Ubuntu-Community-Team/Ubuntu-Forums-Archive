---
title: "how to make apt use update-initramfs instead if initramfs-kpkg?"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2010-03-05
I wonder how one can make apt use update-initramfs instead of initramfs-kpkg?

I have built upstream kernel packages using the instructions here: [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) but whenever I do an apt-get install, it tries and fails to execute initramfs-kpkg on my kernel packages. running mkinitramfs manually runs though just fine...

the man page for initramfs-kpkg mentions that update-initramfs is the current preferred methods. I looked at /etc/apt and /etc/initramfs-tools, but found no way to change what is actually being run.

I also see that initramfs-kpkg and update-initramfs come from the same package, so I can't just simply uninstall the unwanted one either.

any help would be appreciated...

---

