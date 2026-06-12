---
title: "initramdisk placement"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by fotoba on 2011-10-15
Dear Ubuntu experts,

I am familiar with lilo, less familiar with grub a not familiar with grub2.

When I was upgrading to 11.10 I does one fail - after downloading packages I removed network connection. When system reached installation of Adobe flash player I was restarted OS instead of replug the network. Then there was unable to start X.org using nVidia proprietary driver.

My concept of  rescue failed with  usage
update-initramfs
to upgrade init ramdisk for all available kernels. But system does not boot to any of the kernel then with trying to mount ext4 root filesystem. 
In the /boot directory there is no RAMdisk as well as kernel. I am trying to copy kenrl or ramdisk form Live USB of 11.10 to rescue system and use something like

zypper verify  in openSUSE.

to completely rescue system

I am aware of using upgrade with no formatting disk before monday evening , because of parallel installation of the 10.04LTS allows me to do lesson presentation at noon of this day.

Is there anybody to let me some  recombination where to copy ramdisk to boot correctly, please?
Is there anybody to help me with  Ubuntu/Debian alternative to zyppeer verify,please?

I look forward hearing from you. 
Yours faithfully

Peter Fodrek

---

