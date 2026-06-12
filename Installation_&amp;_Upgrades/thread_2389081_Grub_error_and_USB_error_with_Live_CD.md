---
title: "Grub error and USB error with Live CD"
date: 2018-04-11
forum: Installation &amp; Upgrades
---

### Post by eomnden2 on 2018-04-11
Hi,


My computer was working great until one day this message popped up when booting:


```
error: unknown filesystem.
Entering rescue mode...
grub rescue>

```



I searched on the Internet, but no solution using command-line tools worked for me:


```
grub rescue> ls
(hd0) (hd0, msdos1)
grub rescue> ls (hd0,msdos1)/
error: unknown filesystem.
grub rescue> set boot=(hd0,msdos1)
grub rescue> set prefix=(hd0,msdos1)/boot/grub/
grub rescue> insmod normal
error: unknown filesystem.

```

Then I read on the Internet that my grub has to be repaired, using the Ubuntu Live CD or the Boot Repair Disk utiliy.
My computer doesn&#8217;t have a CD drive, I only can use the USB ports. I burned the Ubuntu Desktop Live CD on multiple USB, I burned the Boot Repair Disk utiliy on USBs, but when I want to boot on Ubuntu Live/the utility I always get stuck with this:


```
[    9.192112] tpm tpm0: A TPM error (7) occurred attempting to read a pcr value
[    9.312155] tpm tpm0: A TPM error (7) occurred attempting to read a pcr value
[   11.316021] usb 1-1.5: device descriptor read/64, error -32
[   11.481231] squashfs: SQUASHFS error: unable to read xattr id index table
[   11.504002] usb 1-1.5: device descriptor read/64, error -32
[   11.557747] sd 6:0:0:0: [sdb] No Caching mode page found
[   11.557750] sd 6:0:0:0: [sdb] Assuming drive cache: write through




BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.


(initramfs) [   11.960070] usb 1-1.5: device descriptor read/64, error -32
mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
[   12.564067] usb 1-1.5: device not accepting address 9, error -32
[   13.060065] usb 1-1.5: device not accepting address 10, error -32
[   13.060388] usb 1-1-port5: unable to enumerate USB device



```

Any help would be appreciated!


eomnden2

---

