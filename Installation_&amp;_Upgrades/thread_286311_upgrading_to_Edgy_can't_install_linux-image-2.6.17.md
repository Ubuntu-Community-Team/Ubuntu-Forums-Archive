---
title: "upgrading to Edgy: can't install linux-image-2.6.17-10-386, mkinitramfs 'unsuitable'"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by ticks on 2006-10-27
tried to upgrade from Dapper to Edgy. 

apt gives me this:

Setting up linux-image-2.6.17-10-386 (2.6.17-10.33) ...
Running depmod.
Finding valid ramdisk creators.
Failed to find suitable ramdisk generation tool for kernel version 2.6.17-10-386 on running kernel 2.6.15-27-386 in /usr/sbin/mkinitramfs
dpkg: error processing linux-image-2.6.17-10-386 (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
...

so, what i'd like to know is if anyone has any tips how to install that kernel? first i simply tried to remove it, and then i rebooted, which was a mistake. looks like udevd was upgraded, and it doesn't work with the older kernel. i've got an encrypted (using LUKS) root partition, a home partition and a swap. at boot i get prompted for the password for the root partition, so far so good. i get 'Command successful.' then nothing happens, and after a while i get a bunch of error:

udevd[3792]: add_to_rules: invalid KERNEL operation
udevd[3792]: add_to_rules: invalid rule '/etc/udev/rules.d/z60_usbmount.rules:3'
(and the same for usbmount.rules:4, 5, 6)

then checking root fs works, and reaches Starting early crypto disks, i can't enter my passphrase. it just says:
Enter LUKS passphrase: Command failed: Error reading passphrase
same for Starting remaining crypto disks.

and then fsck fails, because /dev/mapper/cryptohome doesn't exist. 

is there a way to install a new kernel that will make udevd work again? or should i just give up and reinstall?

any help appreciated.

---

### Post by docomo on 2006-10-27
I get the same thing, and I also have an encrypted system. I haven't rebooted yet though.

Update: I managed to fix it. In /etc/kernel-img.conf I had added the line:

ramdisk = /usr/sbin/mkinitramfs

I just removed that line and it worked. No more "Failed to find suitable ramdisk generation tool ..."

For some reason I had to wait a long time after entering my password for the encryption at boottime before anything happended. But then it started up ok, and here I am on Edgy.

---

### Post by docomo on 2006-10-27
ticks: You could start your computer with an Edgy livecd, mount your encrypted root partition, chroot into the encrypted root, and proceed to try and fix the system.

---

### Post by ticks on 2006-10-28
docomo: i managed to install the kernel by doing as you suggested, but i still get the same error when i boot, udevd still isn't happy. any idea what might cause it?

---

