---
title: "Errors after upgrading to 14.04"
date: 2014-06-03
forum: Installation &amp; Upgrades
---

### Post by betty3 on 2014-06-03
After I upgraded the ubuntu version from 13.10 to 14.04 I get this after sudo apt-get upgrade

```
Errors were encountered while processing:
 linux-image-3.11.0-20-generic
 linux-image-3.11.0-22-generic
 linux-image-3.13.0-27-generic
 memtest86+
 grub-pc
 linux-image-extra-3.13.0-27-generic
 linux-image-generic
 linux-generic
 linux
 linux-image-extra-3.11.0-20-generic
 linux-image-extra-3.11.0-22-generic
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

at first I tried to ignore it and go on since it doesn't stop me from doing whatever I want in the computer. 
However now that I'm trying to install ruby it brings these errors again and the installation of new packages is not accomplished. 
Does anyone know what can I do to mend these errors?

---

### Post by philinux on 2014-06-03
From a terminal do this.

```
sudo dpkg --configure -a
```

Post back any errors.

Also do this.

```
sudo update-grub
```

Again post any errors.

---

### Post by betty3 on 2014-06-03
after ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --configure -a
``` I got
[/FONT][/COLOR]```
Setting up memtest86+ (4.20-1.1ubuntu8) ...
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: sony_laptop.kbd_backlight=0: not found
dpkg: error processing package memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-3.13.0-27-generic (3.13.0-27.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.13.0-27-generic
) points to /boot/initrd.img-3.13.0-27-generic
 (/boot/initrd.img-3.13.0-27-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-27-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.13.0-27-generic
) points to /boot/vmlinuz-3.13.0-27-generic
 (/boot/vmlinuz-3.13.0-27-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-27-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: sony_laptop.kbd_backlight=0: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-27-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-27-generic; however:
  Package linux-image-3.13.0-27-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (2.02~beta2-9) ...
/var/lib/dpkg/info/grub-pc.config: 35: /etc/default/grub: sony_laptop.kbd_backlight=0: not found
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on memtest86+; however:
  Package memtest86+ is not configured yet.


dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.11.0-22-generic (3.11.0-22.38) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-22-generic /boot/vmlinuz-3.11.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-22-generic /boot/vmlinuz-3.11.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-22-generic /boot/vmlinuz-3.11.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.11.0-22-generic /boot/vmlinuz-3.11.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.11.0-22-generic /boot/vmlinuz-3.11.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.11.0-22-generic /boot/vmlinuz-3.11.0-22-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: sony_laptop.kbd_backlight=0: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-22-generic.postinst line 1010.
dpkg: error processing package linux-image-3.11.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.27.33); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.11.0-20-generic (3.11.0-20.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: sony_laptop.kbd_backlight=0: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-20-generic.postinst line 1010.
dpkg: error processing package linux-image-3.11.0-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.11.0-20-generic:
 linux-image-extra-3.11.0-20-generic depends on linux-image-3.11.0-20-generic; however:
  Package linux-image-3.11.0-20-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.11.0-20-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-27-generic:
 linux-image-extra-3.13.0-27-generic depends on linux-image-3.13.0-27-generic; however:
  Package linux-image-3.13.0-27-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.13.0-27-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.11.0-22-generic:
 linux-image-extra-3.11.0-22-generic depends on linux-image-3.11.0-22-generic; however:
  Package linux-image-3.11.0-22-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.11.0-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-generic; however:
  Package linux-generic is not configured yet.


dpkg: error processing package linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 memtest86+
 linux-image-3.13.0-27-generic
 linux-image-generic
 grub-pc
 ubuntu-desktop
 linux-image-3.11.0-22-generic
 linux-generic
 linux-image-3.11.0-20-generic
 linux-image-extra-3.11.0-20-generic
 linux-image-extra-3.13.0-27-generic
 linux-image-extra-3.11.0-22-generic
 linux



```

and after ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo update-grub[/FONT][/COLOR]
``` I got :

```

/usr/sbin/grub-mkconfig: 35: /etc/default/grub: sony_laptop.kbd_backlight=0: not found

```

---

### Post by betty3 on 2014-06-03
Thanks for helping me by the way..

---

### Post by betty3 on 2014-06-03
I think that concerning the second command I can go to the file and comment the line "[COLOR=#000000][FONT=Ubuntu Mono]sony_laptop.kbd_backlight=0" but concerning the rest I don't know[/FONT][/COLOR][COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by betty3 on 2014-06-03
well, I had added two lines in the grub file and they were blocking the grub update. I commented them and it worked so now everything is solved. Thanks for the  [COLOR=#000000][FONT=Ubuntu Mono]sudo update-grub command. Without it I wouldn't have noticed that those lines were getting in the way. :)[/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
[/COLOR]
[COLOR=#000000][/COLOR]

---

### Post by philinux on 2014-06-03
Glad it all sorted.

---

