---
title: "Installing 2 kernels"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by neha c on 2007-06-21
Hi,

I am a beginner with ubuntu (and linux itself for that matter). A few  weeks back I installed ubuntu 7.04 feisty fawn. The kernel is 2.6.20 . However, for an academic project I need to work on kernel 2.6.12.3 which is provided by breezy.

I can't see that kernel in synaptic. The breezy options are enabled in the sources list.  How can I install the kernel image for 2.6.12? Is there a way I could add this into synaptic?

I downloaded the kernel from kernel.org. However, compiling it is giving errors.  

Have been stuck for several days now. Would appreciate if someone could tell me how to install this.

Thanks!

---

### Post by mikewhatever on 2007-06-21
It looks like the kernel you are looking for, 2.6.12.3, does not exist. Try [this page]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=2.6.12&searchon=names&subword=1&version=breezy&release=all") for a different version of the Breezy kernel.

---

### Post by bluknight on 2007-06-22
> **neha c said:**
> Hi,
 A few  weeks back I installed ubuntu 7.04 feisty fawn. The kernel is 2.6.20 . However, for an academic project I need to work on kernel 2.6.12.3 which is provided by breezy.


Copy your old kernel and initrd images to Feisty /boot as well as the /lib/modules/kernel and /firmware/kernel files. Then as root do an update-initramfs -c -k kernel as well as your /grub/menu.lst and you shd be able to boot Feisty with the Breezy kernel. See for steps in:
[http://ubuntuforums.org/showthread.php?t=450246&page=2](http://ubuntuforums.org/showthread.php?t=450246&page=2) 

HTH

---

