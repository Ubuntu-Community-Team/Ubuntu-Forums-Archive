---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by limp on 2010-04-23
Hi all,

I am using Ubuntu 9.10 under VMware Workstation 7. 

Every time I do an update, I get this:
```

E: linux-image-2.6.31-15-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-16-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-17-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-19-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-20-generic: subprocess installed post-installation script returned .error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: grub-pc: subprocess installed post-installation script returned error exit status 2

```

By executing ```
sudo dpkg --configure -a
``` I get the following:
```

Setting up linux-image-2.6.31-15-generic (2.6.31-15.50) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-15-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.31-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-19-generic (2.6.31-19.56) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.31-19-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-20-generic (2.6.31-20.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-17-generic (2.6.31-17.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.31-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.31-16-generic (2.6.31-16.53) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-15-generic
 linux-image-2.6.31-19-generic
 linux-image-2.6.31-20-generic
 linux-image-2.6.31-17-generic
 linux-image-generic
 linux-image-2.6.31-16-generic
 grub-pc
 linux-generic

```

Finally, when I try ```
sudo update-grub
``` I get this:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
```

Thanks in advance.

---

### Post by wajdigary on 2011-01-24
i got the same problem.. how can i fix grub-pc?

---

### Post by sikander3786 on 2011-01-24
> **wajdigary said:**
> i got the same problem.. how can i fix grub-pc?
Your issue might not be exactly the same as the OP. Please post the complete output of following command.

Applications > Accessories > Terminal:

```
sudo dpkg --configure -a
```

---

### Post by Don1989 on 2011-03-20
> **limp said:**
> Hi all,

I am using Ubuntu 9.10 under VMware Workstation 7. 

Every time I do an update, I get this:
```

E: linux-image-2.6.31-15-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-16-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-17-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-19-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-20-generic: subprocess installed post-installation script returned .error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: grub-pc: subprocess installed post-installation script returned error exit status 2

```By executing ```
sudo dpkg --configure -a
``` I get the following:
```

Setting up linux-image-2.6.31-15-generic (2.6.31-15.50) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-15-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.31-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-19-generic (2.6.31-19.56) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.31-19-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-20-generic (2.6.31-20.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-17-generic (2.6.31-17.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.31-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.31-16-generic (2.6.31-16.53) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-15-generic
 linux-image-2.6.31-19-generic
 linux-image-2.6.31-20-generic
 linux-image-2.6.31-17-generic
 linux-image-generic
 linux-image-2.6.31-16-generic
 grub-pc
 linux-generic

```Finally, when I try ```
sudo update-grub
``` I get this:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: line 2: All: command not found
/etc/grub.d/README: line 4: 00_*:: command not found
/etc/grub.d/README: line 5: 10_*:: command not found
/etc/grub.d/README: line 6: syntax error near unexpected token `('
/etc/grub.d/README: line 6: `  20_*: Third party apps (e.g. memtest86+).'
```Thanks in advance.

I know this is a bit late but this is how I fixed this problem. Bring up a Shell/Command Prompt/My little pony interface up. (Making up names for Linux items helps with the insanity it causes)

First backup your /etc/grub.d/README file by typing

```
sudo cp /etc/grub.d/README /home/yourusername
```If you want to fix the problem quick and dirty just delete the README file.

```
sudo rm /etc/grub.d/README
```then try updating again



```
sudo apt-get upgrade
```

...and thats all there is to it. Some side notes below.

If you didn't fix this problem before you reboot you will have a unbootable system and will need to use a live cd to go in and fix it going to your root directory and renaming 2 files to get your system boot-able since the kernel is corrupted.

```

sudo mv /initrd.img.old /initrd.img
sudo mv /mvlinuz.old /mvlinuz

```Why did this problem happen? For some reason it is trying to execute the readme in grub. type /etc/grub.d/README and compare to the errors. Posted below.

> /etc/grub.d/README

All executable files in this directory are processed in shell expansion order.

  00_*: Reserved for 00_header.
  10_*: Native boot entries.
  20_*: Third party apps (e.g. memtest86+).

The number namespace in-between is configurable by system installer and/or
administrator.  For example, you can add an entry to boot another OS as
01_otheros, 11_otheros, etc, depending on the position you want it to occupy in
the menu; and then adjust the default setting via /etc/default/grub.
If you REALLY want your readme file back there lol... just "cp" the backup in your home directory there and mess around with the permissions with "chmod". Good luck.

---

