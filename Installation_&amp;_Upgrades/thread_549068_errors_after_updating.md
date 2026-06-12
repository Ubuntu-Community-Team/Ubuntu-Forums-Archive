---
title: "errors after updating"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by Lelouch on 2007-09-12
When i finished updating, I restarted my laptop, and a new third kernel boot loader appeared:

```
title		Ubuntu, kernel 2.6.20-16-lowlatency
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=7f862708-af7c-435f-#b2b0-2531e3b36ed4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=7f862708-af7c-435f-#b2b0-2531e3b36ed4 ro single
initrd		/boot/initrd.img-2.6.20-16-lowlatency
```

i cant load it... (loading X system error) appears.. fortunately, my previous kernel (Ubuntu, kernel 2.6.20-16-general) was still there, so i used it to load my ubuntu...

What is the new kernel boot option?? and why cant i load it??

---

