---
title: "How do I rebuilt restricted modules or compile ati driver to new kernel?"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by Alfie_Alfie on 2008-01-17
Hi, I'm newbie here for ubuntu and linux

I just installed vanilla kernel version 2.6.23.14 followed Master-kernel guide and I cannot access Restricted Driver Manager. After long time with Google I found that I have to rebuilding this module too but I have no idea about it.

Can anyone tell me how to do it please?
I'm not sure but someone told me to compile ati driver into kernel anyway, I also no idea about.

Thanks

Sorry for my Bad English

---

### Post by luisromangz on 2008-01-17
You have to download the ATI drivers from their webpage, and install them using their installer. They contain the source code (although you can't see it) and compile an interface to the kernel for the driver.

---

### Post by zzxt on 2008-01-17
here is guide for what you want,
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Alfie_Alfie on 2008-01-17
> **luisromangz said:**
> You have to download the ATI drivers from their webpage, and install them using their installer. They contain the source code (although you can't see it) and compile an interface to the kernel for the driver.

I follow this guide in method2 [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually)
about 2-3 times but it doesn't work (error when compiling)

Error! Your kernel source for kernel 2.6.23.14 cannot be found at
/lib/modules/2.6.23.14/build or /lib/modules/2.6.23.14/source.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.23.14 (x86_64) first.
Done.

This guide show me how to compiling driver to kernel? (like you guys said? I think I've got more idea, Just a little)

---

