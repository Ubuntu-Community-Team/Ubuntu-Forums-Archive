---
title: "Cannot upgrade Kernel on 14.04 - Disk does not exist, so falling back to partition..."
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by lincoln6ix on 2015-06-21
I've upgraded from 10.04 to 14.04.

My server is still showing Kernel version ```
2.6.32-22-server
```

I've installed the latest kernels by running ```
$ sudo apt-get install linux-generic
```

I then run ```
$ sudo update-grub
```

And I get a number of warnings: 

```
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-2.6.32-22-server
Found initrd image: /boot/initrd.img-2.6.32-22-server
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.

```
And after a reboot the server is still using the 2.6 Kernel.

Can anyone help me resolve this so that I can update to the latest Kernel? Do I just need to remove the old kernels, and reconfigure Grub to use the latest ones?

Thanks in advance

---

### Post by PaulW2U on 2015-06-21
Please use standard fonts and colours wherever possible as some users may find coloured text difficult to read.

The use of CODE tags can be used to highlight input and responses.

---

