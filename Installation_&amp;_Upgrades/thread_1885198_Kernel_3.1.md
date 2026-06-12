---
title: "Kernel 3.1"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by chazdg24 on 2011-11-22
Question, is there a way to remove kernel 3.1 from Oneiric?

I upgraded to 3.1 by compiling it with these instructions:

Open the terminal and run these two commands for both 32-bit and 64-bit versions of Ubuntu 11.10/11.04:

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-headers-3.1.0-030100_3.1.0-030100.201110241006_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-headers-3.1.0-030100_3.1.0-030100.201110241006_all.deb)

sudo dpkg -i linux-headers-3.1.0-030100_3.1.0-030100.201110241006_all.deb

Ubuntu (64-bit)

For Ubuntu 11.10/11.04 (64-bit), issue these commands:

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb)

sudo dpkg -i linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-image-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-image-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb)

sudo dpkg -i linux-image-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb


Everything went well.  I was able to reboot quickly, but Firefox and Chrome constantly crash with Kernel 3.1.  I am using Gnome 3.2 and saw improvement with 3.0.0.13 provided by ppa.  Any help with 3.1 or just removing it would be helpful.  Thanks to all that reply.

---

### Post by lswb on 2011-11-22
Assuming you still have 3.0.0 or some other kernel installed that works OK for you, you can just sudo dpkg -r name_of_the_kernel_image_package_you_want_to_remove (dpkg -p ... will also work) and then you can do the same for the 2 header packages. Instead of typing out the long package names, you may find it easier (I do) to use synaptic to search for the kernel names you want to remove, mark them for removal or "complete removal" (equivalent to the -p --purge option to dpkg) and uninstall from there.

---

