---
title: "QEMU Installation"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by MocroNL on 2012-12-19
Hey guys I'am trying to install QEMU on ubuntu 11.10. My CPU does not support hardware virtualization but it should not matter with QEMU.

I'am using this guide: [http://www.upubuntu.com/2012/03/how-to-install-android-x86-40-using.html](http://www.upubuntu.com/2012/03/how-to-install-android-x86-40-using.html)

When I try and start the installation process using this command(kvm -m 512 -cdrom android-x86-4.0.iso -hda android-4.0.img -boot d) It gets stuck...

root@TLS-AMS-FB-01:~/android-x86# kvm -m 512 -cdrom android-x86-4.0.iso -hda android-4.0.img -boot d
open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support
init kbd.

After this nothing new pops up... Does anyone had this problem in the past or knows a solution to this?

Many thanks!

---

