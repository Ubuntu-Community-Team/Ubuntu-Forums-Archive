---
title: "Having trouble installing anything"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by sumpm1 on 2008-09-11
I recently had trouble installing anything from synaptic, command, or .deb installer. I was constantly getting an error for "libsoup2.4.1 is missing newline" or something like that. I followed the directions in this thread: [http://ubuntuforums.org/showthread.php?t=592576](http://ubuntuforums.org/showthread.php?t=592576) to fix libsoup. Now I get the following errors when trying to install: And these errors come up for ANYTHING to install. I don't know how I am to try and update the kernel. But these errors came AFTER I fixed another package, what gives?

[[IMG]http://img137.imageshack.us/img137/6171/screenshothi9.png[/IMG]](http://imageshack.us)
[[IMG]http://img137.imageshack.us/img137/screenshothi9.png/1/w524.png[/IMG]](http://g.imageshack.us/img137/screenshothi9.png/1/)

---

### Post by Pumalite on 2008-09-11
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
(post outputs)

---

### Post by sumpm1 on 2008-09-12
Well, I had already UNINSTALLED the last 3 packages on the list and the only thing left was the kernel. So here is the output:

```
dave@dave-desktop:~$ sudo dpkg --configure -a
[sudo] password for dave: 
Setting up linux-image-2.6.24-19-generic (2.6.24-19.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.36 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.36 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
User postinst hook script [/sbin/update-grub] exited with value 10
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
dave@dave-desktop:~$ 


```

---

