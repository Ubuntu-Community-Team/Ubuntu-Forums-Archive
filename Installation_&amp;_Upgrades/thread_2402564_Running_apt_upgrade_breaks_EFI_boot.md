---
title: "Running apt upgrade breaks EFI boot"
date: 2018-10-01
forum: Installation &amp; Upgrades
---

### Post by hvxl on 2018-10-01
After running apt upgrade, several critical files have been removed from /boot/efi/EFI/ubuntu, resulting in a non-bootable system. Here is a log of what happens:

```
root@beelink:~# ls -l /boot/efi/EFI/ubuntu/
total 3400
-rwx------ 1 root root     108 Sep 27 03:43 BOOTX64.CSV
-rwx------ 1 root root     117 Sep 27 03:43 grub.cfg
-rwx------ 1 root root 1116024 Sep 27 03:43 grubx64.efi
-rwx------ 1 root root 1153336 Sep 27 03:43 mmx64.efi
-rwx------ 1 root root 1196736 Sep 27 03:43 shimx64.efi
root@beelink:~# apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done

[snip]

Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for initramfs-tools (0.130ubuntu3.3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-34-generic
update-initramfs: Generating /boot/efi/EFI/ubuntu/shimx64.efi
Processing triggers for linux-image-4.15.0-36-generic (4.15.0-36.39) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-36-generic
update-initramfs: Generating /boot/efi/EFI/ubuntu/shimx64.efi
/etc/kernel/postinst.d/zz-update-grub:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-36-generic
Found initrd image: /boot/initrd.img-4.15.0-36-generic
Found linux image: /boot/vmlinuz-4.15.0-34-generic
Found initrd image: /boot/initrd.img-4.15.0-34-generic
Adding boot menu entry for EFI firmware configuration
done
root@beelink:~# ls -l /boot/efi/EFI/ubuntu/
total 62360
-rwx------ 1 root root 63852974 Oct  1 14:40 shimx64.efi
root@beelink:~#
```
I have to run grub-install to recreate the grubx64.efi, grub.cfg etc files to make the system bootable again. It's very easy to forget that step and then the system doesn't boot. How can I make sure that I'm always automatically left with a bootable system after running apt upgrade?

This is 18.04.1 LTS (Bionic Beaver) running on a Beelink-S1 mini PC.

---

### Post by oldfred on 2018-10-01
Your new shim looks very large?

I just ran same updates to 4.15.0-36-generic and there was no change to files in my ESP.

```
fred@bionic-z97:~$ ls -l /boot/efi/EFI/ubuntu/
total 3400
-rwxr-xr-x 1 root root     108 Sep 16 15:53 BOOTX64.CSV
-rwxr-xr-x 1 root root     126 Sep 16 15:53 grub.cfg
-rwxr-xr-x 1 root root 1116024 Sep 16 15:53 grubx64.efi
-rwxr-xr-x 1 root root 1153336 Sep 16 15:53 mmx64.efi
-rwxr-xr-x 1 root root 1196736 Sep 16 15:53 shimx64.efi

```

---

### Post by hvxl on 2018-10-03
> **oldfred said:**
> Your new shim looks very large?
You're right! I hadn't noticed that. Next time it happens I will have a closer look to see if I can recognize anything inside.

---

