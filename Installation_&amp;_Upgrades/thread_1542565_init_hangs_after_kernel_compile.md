---
title: "init hangs after kernel compile"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by -Duvel- on 2010-07-30
I compiled a kernel from source and I installed it manually.

The boot sequence hangs after mount_all
I managed to get my system to boot properly after I created an executable file /sbin/i and passed this as init= argument on the boot command line.


# cat /sbin/i
#!/bin/bash
exec init

# grep /sbin/i /boot/grub/menu.lst
kernel          /vmlinuz root=/dev/mapper/ubuntu-root ro init=/sbin/i


I'm wondering what went wrong and how I can fix this "properly". Any help appreciated

---

