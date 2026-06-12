---
title: "How to prevent loading useless kernel modules?"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by erzhong on 2005-05-01
I used lsmod to check the kernel modules loaded and found things such as sony_acpi (I am using a IBM T42...).

How can I prevent my laptop from loading these modules at boot time?  I can not find them in the kernel modules configuration files in /etc.  

Thank you!

---

### Post by Nis on 2005-05-03
Add the module name to /etc/hotplug/blacklist to prevent it from being loaded at boot (unless another module requires it to be loaded.  Then it will automatically be loaded).

---

### Post by erzhong on 2005-05-04
Thank you for you answer.

I put the name of the modules in the blacklist, but they are still loaded when I reboot.  I can remove them by rmmod, which means they are not in use and not required by other modules.  

Maybe I need to make a script and put it in rc3.d to remove all the unnecessary modules after boot.

---

### Post by cutOff on 2005-05-04
maybe you should try modconf utility.

[http://packages.debian.org/testing/base/modconf](http://packages.debian.org/testing/base/modconf)

---

