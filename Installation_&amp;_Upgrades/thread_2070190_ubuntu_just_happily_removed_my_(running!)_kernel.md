---
title: "ubuntu just happily removed my (running!) kernel"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by surfer on 2012-10-12
this is not a help request; i was able to fix the problem. but does anyone know why i was able to remove the kernel i was running just with the small warning
```
WARN: Proceeding with removing running kernel image.
```
but no prompt to confirm that? i seem to remember that i had been prompted on older ubuntu versions when i tried to do just that.

here is what i did: i tried to remove the old kernels i had installed with
```
$ sudo apt-get remove --purge linux-image-3.2.0-2*
```
hoping that the  [FONT="Courier New"]linux-image-3.2.0-30-generic linux-image-3.2.0-31-generic linux-image-3.2.0-32-generic[/FONT] kernels would be kept. i didn't take a close look at what would all be removed and removed ALL THE KERNELS of my system that way (fortunately i noticed this right afterwards and reinstalled the latest kernel).

and here's the log (notice the last line: there is no kernel in /boot):

```
surfer@hiro:~$ sudo apt-get remove --purge linux-image-3.2.0-2*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-3.2.0-29-generic' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-23-lowlatency-pae' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-24-virtual' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-30-powerpc64-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-25-powerpc64-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-30-highbank' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-25-highbank' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-29-powerpc-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1418-omap4' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1603-armadaxp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1609-armadaxp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-29-omap' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-32-virtual' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-27-virtual' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-24-generic' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-32-omap' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-27-omap' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-30-generic-pae' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-25-generic-pae' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-30-omap' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-25-omap' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-31-powerpc-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-26-powerpc-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-23-omap' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1416-omap4' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-32-generic' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-27-generic' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-23-powerpc-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1414-omap4' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1602-armadaxp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1608-armadaxp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-32-powerpc64-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-27-powerpc64-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-23-lowlatency' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1412-omap4' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-29-generic-pae' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-24-powerpc64-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-30-virtual' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-25-virtual' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-29-highbank' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1607-armadaxp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-31-generic-pae' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-26-generic-pae' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-32-powerpc-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-27-powerpc-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-30-generic' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-25-generic' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-23-generic-pae' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-24-powerpc-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1419-omap4' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-29-powerpc64-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1606-armadaxp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1417-omap4' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-31-omap' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-26-omap' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-23-virtual' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-24-omap' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-31-powerpc64-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-26-powerpc64-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-32-highbank' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-27-highbank' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1420-omap4' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1415-omap4' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-23-powerpc64-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-31-virtual' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-26-virtual' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-32-generic-pae' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-27-generic-pae' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-23-generic' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1605-armadaxp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-1413-omap4' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-24-generic-pae' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-30-powerpc-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-25-powerpc-smp' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-29-virtual' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-31-generic' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-26-generic' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-31-highbank' for regex 'linux-image-3.2.0-2*'
Note, selecting 'linux-image-3.2.0-26-highbank' for regex 'linux-image-3.2.0-2*'
Package linux-image-3.2.0-23-generic is not installed, so not removed
Package linux-image-3.2.0-23-virtual is not installed, so not removed
Package linux-image-3.2.0-23-lowlatency is not installed, so not removed
Package linux-image-3.2.0-24-generic is not installed, so not removed
Package linux-image-3.2.0-24-virtual is not installed, so not removed
Package linux-image-3.2.0-25-virtual is not installed, so not removed
Package linux-image-3.2.0-26-virtual is not installed, so not removed
Package linux-image-3.2.0-27-virtual is not installed, so not removed
Package linux-image-3.2.0-29-virtual is not installed, so not removed
Package linux-image-3.2.0-30-virtual is not installed, so not removed
Package linux-image-3.2.0-31-virtual is not installed, so not removed
Package linux-image-3.2.0-32-virtual is not installed, so not removed
The following packages were automatically installed and are no longer required:
  wireless-regdb iw crda
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic* linux-image-3.2.0-25-generic* linux-image-3.2.0-26-generic*
  linux-image-3.2.0-27-generic* linux-image-3.2.0-29-generic*
  linux-image-3.2.0-30-generic* linux-image-3.2.0-31-generic*
  linux-image-3.2.0-32-generic* linux-image-generic*
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
After this operation, 149 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 285333 files and directories currently installed.)
Removing linux-generic ...
Removing linux-image-3.2.0-25-generic ...
Purging configuration files for linux-image-3.2.0-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
Removing linux-image-3.2.0-26-generic ...
Purging configuration files for linux-image-3.2.0-26-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
Removing linux-image-3.2.0-27-generic ...
Purging configuration files for linux-image-3.2.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
Removing linux-image-3.2.0-29-generic ...
Purging configuration files for linux-image-3.2.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
Removing linux-image-3.2.0-30-generic ...
Purging configuration files for linux-image-3.2.0-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
Removing linux-image-3.2.0-31-generic ...
Purging configuration files for linux-image-3.2.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
Removing linux-image-generic ...
Removing linux-image-3.2.0-32-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.2.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic 

surfer@hiro:~$ ls /boot/
grub  memtest86+.bin  memtest86+_multiboot.bin


```

---

