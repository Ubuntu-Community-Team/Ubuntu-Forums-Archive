---
title: "Dual Boot Windows 7 + Parted Magic problem"
date: 2016-02-26
forum: Installation &amp; Upgrades
---

### Post by exus69 on 2016-02-26
Hello friends,

Am dual booting for the first time in my life. Have installed Windows 7 on C drive. Am trying to dual boot with parted magic using unetbootin but am stuck.
So here is what I did step by step:

1) Booted into Windows 7
2) In unetbootin selected parted magic iso
3) Type: Hard Disk, Drive: C:\

After reboot I get two options "Windows 7" and "unetbootin". After selecting unetbootin I get stuck
at the following:

losetup: /dev/loop252: No such file or directory
mount: unknown filesystem type 'squashfs'
Mounting the fu.sqfs failed

I am trying to follow this link [https://partedmagic.com/frugal-install/](https://partedmagic.com/frugal-install/) since I cannot install it directly from the live usb to the hdd. 
The problem is the second step from the above link. I cannot find /etc/grub.d/40_custom (Grub2) since am booted into Windows 7.
I think I need to make some changes to the menu as described in bold in that link but am unable to find it through Windows.

Please help

---

