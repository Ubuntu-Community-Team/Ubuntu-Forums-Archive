---
title: "Guide to install 4.9 rc2 kernel with 16.04?"
date: 2016-10-29
forum: Installation &amp; Upgrades
---

### Post by mordec4i on 2016-10-29
I need a guide how to install the latest kernel because I tried following a couple that I found on google and all of them eventually give me errors.

---

### Post by mets_web on 2016-10-29
[https://github.com/mtompkins/linux-kernel-utilities](https://github.com/mtompkins/linux-kernel-utilities)

Using the [update_ubuntu_kernel.sh]("https://github.com/mtompkins/linux-kernel-utilities/blob/master/update_ubuntu_kernel.sh") script

In the variables file set RC_FILTER=" " (space).

Here's a video with some example: [https://www.youtube.com/watch?v=CokrHUykkUQ](https://www.youtube.com/watch?v=CokrHUykkUQ)

---

### Post by mordec4i on 2016-10-30
Unfortunately didn't work for me. When I reboot the PC, I get the ubuntu login page with some "system failure" message and when I enter my login password the page just loops and never logs into ubuntu. This has been happening to me all day. Secondly, do I have to install the latest nvidia before doing the kernel update? In either case I tried both ways and always get the same problem after the kernel update and reboot of the pc.

---

### Post by mets_web on 2016-10-30
Abstracts like "some system failure" aren't terribly helpful for those trying to assist. Without explicit information, everything is a guess and that isn't the best way forward.
It seems you've successfully updated the kernel - so to say "didn't work for me" is ambiguous at best. 
You'll need to give exacting messages during a boot cycle so it can be isolated as to whether the cause is your desktop environment of choice or something else would be the next step.

---

### Post by mordec4i on 2016-10-30
Ok well today I reinstalled 16.04 and did the steps again from the video above that you provided. Now my system booted but there was a few errors during install and now my wifi doesn't work. I tried enabling the broadcom wifi driver in the additional drivers but it just reverts back to the generic.

The method above install 4.8.0 kernel.

During install this is what it said:

> [+] Installing kernel . . .
Selecting previously unselected package linux-headers-4.8.0-040800.
(Reading database ... 208009 files and directories currently installed.)
Preparing to unpack linux-headers-4.8.0-040800_4.8.0-040800.201610022031_all.deb ...
Unpacking linux-headers-4.8.0-040800 (4.8.0-040800.201610022031) ...
Selecting previously unselected package linux-headers-4.8.0-040800-generic.
Preparing to unpack linux-headers-4.8.0-040800-generic_4.8.0-040800.201610022031_amd64.deb ...
Unpacking linux-headers-4.8.0-040800-generic (4.8.0-040800.201610022031) ...
Selecting previously unselected package linux-image-4.8.0-040800-generic.
Preparing to unpack linux-image-4.8.0-040800-generic_4.8.0-040800.201610022031_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.8.0-040800-generic /boot/vmlinuz-4.8.0-040800-generic
Done.
Unpacking linux-image-4.8.0-040800-generic (4.8.0-040800.201610022031) ...
Setting up linux-headers-4.8.0-040800 (4.8.0-040800.201610022031) ...
Setting up linux-headers-4.8.0-040800-generic (4.8.0-040800.201610022031) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.8.0-040800-generic /boot/vmlinuz-4.8.0-040800-generic
**Error! Bad return status for module build on kernel: 4.8.0-040800-generic (x86_64)**
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
Setting up linux-image-4.8.0-040800-generic (4.8.0-040800.201610022031) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-040800-generic /boot/vmlinuz-4.8.0-040800-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.8.0-040800-generic /boot/vmlinuz-4.8.0-040800-generic
[B]ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 4.8.0-040800-generic (x86_64)[/B]
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-040800-generic /boot/vmlinuz-4.8.0-040800-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-040800-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.8.0-040800-generic /boot/vmlinuz-4.8.0-040800-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-040800-generic /boot/vmlinuz-4.8.0-040800-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-040800-generic /boot/vmlinuz-4.8.0-040800-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-040800-generic /boot/vmlinuz-4.8.0-040800-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-040800-generic
Found initrd image: /boot/initrd.img-4.8.0-040800-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found Windows Boot Manager on /dev/sdc3@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done



---

### Post by mets_web on 2016-10-30
I'd suggest opening a new thread for this problem in the Networking & Wireless section.
It seems you need some of the Broadcom specific packages for your installation and you're likely to find better help there.

That info above is also helpful.
This file is likely useful to help track it down: [COLOR=#000000]*/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log*[/COLOR]

---

