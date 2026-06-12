---
title: "Cannot install and UPGRADE from 20.04 TO 22.04"
date: 2022-10-24
forum: Installation &amp; Upgrades
---

### Post by bunnyppl on 2022-10-24
Getting the following error 

```

I: /boot/initrd.img.old is now a symlink to initrd.img-5.15.0-46-generic
Setting up linux-image-5.15.0-52-generic (5.15.0-52.58) ...
I: /boot/initrd.img is now a symlink to initrd.img-5.15.0-52-generic
Processing triggers for doc-base (0.11.1) ...
Processing 1 changed doc-base file...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for initramfs-tools (0.140ubuntu13) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-50-generic
cp: cannot stat '/etc/fonts/fonts.conf': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.15.0-50-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.15.0-46-generic (5.15.0-46.49) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.15.0-46-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-46-generic
cp: cannot stat '/etc/fonts/fonts.conf': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.15.0-46-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.15.0-46-generic (--configure):
 installed linux-image-5.15.0-46-generic package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.15.0-52-generic (5.15.0-52.58) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.15.0-52-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-52-generic
cp: cannot stat '/etc/fonts/fonts.conf': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.15.0-52-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.15.0-52-generic (--configure):
 installed linux-image-5.15.0-52-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
 linux-image-5.15.0-46-generic
 linux-image-5.15.0-52-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by mIk3_08 on 2022-10-24
Try to run this command below and please post the results here in thread wrap with code. Regards and cheers
```
sudo apt --fix-broken install
```

---

### Post by bunnyppl on 2022-10-24
I did run 

```

sudo apt --fix-broken install
```

```

Processing triggers for initramfs-tools (0.140ubuntu13) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-50-generic
cp: cannot stat '/etc/fonts/fonts.conf': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.15.0-50-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.15.0-46-generic (5.15.0-46.49) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.15.0-46-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-46-generic
cp: cannot stat '/etc/fonts/fonts.conf': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.15.0-46-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.15.0-46-generic (--configure):
 installed linux-image-5.15.0-46-generic package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.15.0-52-generic (5.15.0-52.58) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.15.0-52-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-52-generic
cp: cannot stat '/etc/fonts/fonts.conf': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.15.0-52-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.15.0-52-generic (--configure):
 installed linux-image-5.15.0-52-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
 linux-image-5.15.0-46-generic
 linux-image-5.15.0-52-generic



```

---

### Post by bunnyppl on 2022-10-24
```

&#10140; sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-5.15.0-50-generic
cp: cannot stat '/etc/fonts/fonts.conf': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.15.0-50-generic with 1.



```

---

### Post by bunnyppl on 2022-10-24
try this also no luck 

```

[COLOR=#333333][FONT=monospace]apt purge --reinstall plymouth
[/FONT][/COLOR]
```

---

### Post by Rick St. George on 2022-10-24
For what it's worth ... I've been told several times in this forum;

It is best to do a clean install.

1) Download the new version (with desktop of choice Ubuntu, Xubuntu, UbuntuStudio, etc.) and burn to DVD.

2) Do a Fresh install from the disk and let it do what it needs to do in the partition of your choice, or select default.

3) If backups were made of all Docs, Music, etc. | Copy them back to your Home directory.

Enjoy Ubuntu ;-)

---

### Post by mIk3_08 on 2022-10-25
Run the following command below: then show the result here in thread. Regards and cheers.
```
sudo apt autoclean
``` then
```
sudo apt autoremove
``` then last
```
sudo apt --purge remove
```
```
sudo dpkg --purge --force-all 
```

---

### Post by bunnyppl on 2022-10-28
I did solve it by reinstalling ubuntu desktop

---

