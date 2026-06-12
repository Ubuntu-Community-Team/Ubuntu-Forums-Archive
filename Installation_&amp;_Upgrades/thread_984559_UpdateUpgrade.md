---
title: "Update/Upgrade"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by Jeeks on 2008-11-16
Hello

After running "sudo apt-get update" where there is absolutely no problem, I run the command that usually follows "sudo apt-get upgrade" and I encounter the following error:

```
Do you want to continue [Y/n]? y
(Reading database ... 180614 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-21-generic 2.6.24-21.42 (using .../linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-21-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.24-21-generic': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /vmlinuz-2.6.24-18-generic
Found kernel: /vmlinuz-2.6.24-17-generic
Found kernel: /vmlinuz-2.6.24-16-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What shall I do to fix this?

---

### Post by oldos2er on 2008-11-16
"No space left on device" means you're out of hard disk space. See if you can resize your partition to something larger.

---

### Post by Jeeks on 2008-11-17
Problem solved, I had to delete old linux kernel images lying in /boot.

You can bag the thread.

---

