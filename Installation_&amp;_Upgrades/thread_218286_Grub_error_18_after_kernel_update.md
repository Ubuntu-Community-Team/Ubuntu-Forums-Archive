---
title: "Grub error 18 after kernel update"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by my3ke on 2006-07-18
Hi all,

This one is confounding ](*,) me as I am able to boot with the previous kernel (2.6.15-25-386/686), but when I boot with the newest kernel (2.6.15-26-..), I get the following:

"Error 18:  Selected cylinder exceeds maximum support by BIOS"

I'm not sure why this is happening since I've never had a problem before.  Is there a safe way to uninstall the last version of the kernel without breaking this machine.

thanks,
my3ke

---

### Post by linuxnewbie946 on 2006-07-18
```
dpkg -r YOUR KERNEL NAME
```

that may work........ not sure

---

