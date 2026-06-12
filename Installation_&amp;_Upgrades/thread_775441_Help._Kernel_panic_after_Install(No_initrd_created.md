---
title: "Help. Kernel panic after Install(No initrd created)."
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Xorcerer on 2008-04-30
I have just changed my main OS from PCLinuxOS to Ubuntu 8.04.
The liveCD works well and the installation is smooth. But after I reboot the Machine, it stopped at Kernel panic. Some word like unable to read unknown block (0,0).
My root partition type is Reiserfs.
I found out that there is only 3 line for one option. No initrd file is declared.
here is part of the menu.lst.
```

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=4884e3f4-dd2f-4e04-a156-41701f51657b ro quiet splash locale=en_US
quiet

```
I found that there is only one initrd file in the /boot, named initrd.img-2.6.24-16-generic.bak.
And if I added a new line with the initrd file in the grub. It works without a splash but in textmode.
Then I tried to install a new kernel(realtime kernel) with apt, it was failed to boot again with the same problem, no initrd. and the initrd.img-2.6.24-16-generic.bak can only use for the generic kernel.
Thanks.
This is my first post here.

---

### Post by Xorcerer on 2008-05-01
Any body?
Is the Reiserfs not supported to be the /boot?

---

