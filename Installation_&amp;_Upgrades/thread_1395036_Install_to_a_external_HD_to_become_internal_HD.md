---
title: "Install to a external HD to become internal HD"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by maeztro on 2010-01-31
I have an older laptop with a broken CD drive so I cannot boot the CD Drive with my ubuntu image. The laptop does not support booting from a USB drive either.
 
So what I did was take the HD out of the laptop and using a USB enclosure plugged it in to my Win7 desktop. Then I booted from my Ubuntu CD and had Ubuntu install on the USB Drive. 
 
Took the USB drive off, and put it back in the laptop. It seems to work except it looks like it was installed with my desktop hardware. Also, every time it boots it starts at a recovery screen asking if for several boot options (including win7 which does not exist on the laptop!).
 
So I assume I did something wrong along the way. Any tips on how I can do this correctly?
 
Thanks in advance,
M

---

### Post by milton1 on 2010-01-31
It is normal to get a boot screen with several options. It just happens that the system is looking for some boot options from the installing machine. Next time you have the system running, go to a terminal and try the following:
```

sudo grub-mkdevicemap && sudo update-grub

```

---

