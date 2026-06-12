---
title: "vmware player on Gutsy (7.10)"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by cayhorstmann on 2007-10-13
After I upgraded from Feisty to Gutsy, The vmware player stopped working. I get an error message "Could not open /dev/vmmon. Please make sure that the kernel module `vmmon' is loaded".

Ok.

How do I make sure?

Thanks,

Cay

---

### Post by EclipseAgent on 2007-10-13
> **cayhorstmann said:**
> After I upgraded from Feisty to Gutsy, The vmware player stopped working. I get an error message "Could not open /dev/vmmon. Please make sure that the kernel module `vmmon' is loaded".

Ok.

How do I make sure?

Thanks,

Cay

Since you recompiled your kernel, you'll have to recompile the VMWare Kernel Modules into the kernel by running the vmware-config.pl script.

---

### Post by cayhorstmann on 2007-10-13
Thanks for your note. 

With the player module that came with Feisty, there was no such script. They only had a network configuration script. 

But it turns out that VMWare generously provides the free player on their website [http://www.vmware.com/products/player/](http://www.vmware.com/products/player/). I was able to download and install it without a hitch--not even that vmware-any-any patch that was described here ([http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html](http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html)). The only drawback--I will need to recompile the kernel module with every kernel update, at least until Gutsy starts including the kernel modules.

---

