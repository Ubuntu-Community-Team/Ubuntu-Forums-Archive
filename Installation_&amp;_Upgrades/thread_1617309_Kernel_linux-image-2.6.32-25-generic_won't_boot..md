---
title: "Kernel linux-image-2.6.32-25-generic won't boot."
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by JimGvo on 2010-11-09
This is what's installed:

>  aptitude search linux-image | grep generic
i   linux-image-2.6.32-21-generic   - Linux kernel image for version 2.6.32 on x
p   linux-image-2.6.32-21-generic-p - Linux kernel image for version 2.6.32 on x
p   linux-image-2.6.32-22-generic   - Linux kernel image for version 2.6.32 on x
p   linux-image-2.6.32-22-generic-p - Linux kernel image for version 2.6.32 on x
p   linux-image-2.6.32-23-generic   - Linux kernel image for version 2.6.32 on x
p   linux-image-2.6.32-23-generic-p - Linux kernel image for version 2.6.32 on x
i   linux-image-2.6.32-24-generic   - Linux kernel image for version 2.6.32 on x
p   linux-image-2.6.32-24-generic-p - Linux kernel image for version 2.6.32 on x
i   linux-image-2.6.32-25-generic   - Linux kernel image for version 2.6.32 on x
p   linux-image-2.6.32-25-generic-p - Linux kernel image for version 2.6.32 on x
i   linux-image-generic             - Generic Linux kernel image                
p   linux-image-generic-pae         - Generic Linux kernel image   

Short story, I'm running 32.24 because 32.25 fails to boot.  I see the Grub menu, select the -25 kernel, the screen blanks, a cursor appears in the top left and nothing.

Long story.

I was attempting to install an OpenVZ kernel based on the -25 kernel (vmlinuz-2.6.32.25-openvz) and successfully built it but when I attempted to boot, I received the message:

EXT3 -FS sda5 couldn't mount because of unsupported optional features (240)

 and others that may or may not have any impact.

I initially suspected that the ext4 wasn't built into the kernel but when I looked at the .config file, I see:

> CONFIG_EXT4_FS=y
CONFIG_EXT4_FS_XATTR=y
CONFIG_EXT4_FS_POSIX_ACL=y
CONFIG_EXT4_FS_SECURITY=y
# CONFIG_EXT4_DEBUG is not set


That's when I tried to boot the generic kernel. Since it didn't boot either I decided there might be something about the -25, and not the openvz kernel.

Anyone care to comment or make as suggestion?

Jim.

---

