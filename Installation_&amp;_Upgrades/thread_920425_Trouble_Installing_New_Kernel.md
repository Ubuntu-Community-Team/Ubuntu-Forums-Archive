---
title: "Trouble Installing New Kernel"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by NuNn DaDdY on 2008-09-15
After successfully compiling my kernel I am encountering problems when I try to install.  Here is what it is saying


dpkg: error processing linux-image-2.6.26.5-custom-one_2.6.26.5-custom-one-10.00.Custom_i386.deb (--install):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.26.5-custom-one/kernel/net/bridge/netfilter/ebt_among.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by eldragon on 2008-09-15
seems like youve run out of disk space, see what 
```

$ df -h /

```

outputs..

---

### Post by NuNn DaDdY on 2008-09-16
Here is what df -h shows:

/dev/sda2             6.5G  4.3G  2.0G  69% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   44K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      6.5G  4.3G  2.0G  69% /home/corey/.gvfs

---

### Post by Pumalite on 2008-09-16
Post the output of:
sudo dpkg --configure -a

---

