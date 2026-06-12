---
title: "Install and patch older kernel"
date: 2015-05-07
forum: Installation &amp; Upgrades
---

### Post by Jnetty99 on 2015-05-07
Ubuntu 14.04.2 32bit with Kernel 3.16. 

I was giving a hardware patch to test something and had to rebuild the kernel and that all went well. I can hit SHIFT at boot up and select the new Kernel 3.16-test. 

But now I have been given a patch for Kernel 3.10.74. 

Was wondering if I can put older kernel in the system and could it be patched? 

I did attempt to do this and I don’t think I did this well. 

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.74-saucy/linux-headers-3.10.74-031074_3.10.74-031074.201504131044_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.74-saucy/linux-headers-3.10.74-031074-generic_3.10.74-031074.201504131044_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.74-saucy/linux-image-3.10.74-031074-generic_3.10.74-031074.201504131044_i386.deb

sudo dpkg -i *.deb
```

restarts, SHIFT and booted to 3.10.74 Generic

This is where not sure how to patch and I guess rebuild kernel with patch. 

I was given instructions before to run the patch at ```
/usr/src/linux-3.16/
``` 
So i thought i could do similar thing and i went to ```
/usr/src/linux-headers-3.10.74-031074-generic/
``` 

I got errors that could find what to patch. 

I'm not a Linux expert, but someone really trying to learn Linux and become better at it. 

Thank you for anyone that has any suggestions.

---

### Post by dino99 on 2015-05-07
The main howtos
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[http://unix.stackexchange.com/questions/58229/automatically-apply-module-patch-and-compile-kernel-when-updated](http://unix.stackexchange.com/questions/58229/automatically-apply-module-patch-and-compile-kernel-when-updated)

---

### Post by Jnetty99 on 2015-05-07
> **dino99 said:**
> The main howtos
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[http://unix.stackexchange.com/questions/58229/automatically-apply-module-patch-and-compile-kernel-when-updated](http://unix.stackexchange.com/questions/58229/automatically-apply-module-patch-and-compile-kernel-when-updated)

Thanks, I will check them out.

---

