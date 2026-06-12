---
title: "dist-upgrade for karmic os failure"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bwallum on 2009-09-14
Hi

I thought I would try to help out with karmic testing and used a terminal for sudo apt-get dist-upgrade having set all my software sources to karmic.

After about an hour I went through a few dialogues and rebooted. The result was a black screen with the underscore cursor flashing. Left it for twenty minutes, no change so rebooted. No change, rebooted again and again no change.

I'm now using my external drive and jaunty to boot and diagnose. However, I think I need like some help to get the repair underway. Any offers please?

---

### Post by linux6994 on 2009-09-14
Look here and see if it helps, also search this forum for "flashing cursor.

[http://ubuntuforums.org/showthread.php?t=1166802&highlight=flashing+cursor](http://ubuntuforums.org/showthread.php?t=1166802&highlight=flashing+cursor)

---

### Post by bwallum on 2009-09-14
mmmmm ....still stuck

---

### Post by terry_gardener on 2009-09-14
check out bug report

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/429003]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/429003")

you need to downgrade the libc6 packages 

sudo dpkg -i --force-downgrade /var/cache/apt/archives/libc6_2.10.1-0ubuntu9_i386.deb
sudo dpkg -i --force-downgrade /var/cache/apt/archives/libc6-i686_2.10.1-0ubuntu9_i386.deb
sudo dpkg -i --force-downgrade /var/cache/apt/archives/libc6-dev_2.10.1-0ubuntu9_i386.deb

---

### Post by bwallum on 2009-09-14
I'm on AMD64..

---

### Post by terry_gardener on 2009-09-14
you could try changing the xorg.conf file, device section, change the driver to nv from nvidia and then reboot.

---

### Post by terry_gardener on 2009-09-14
also checkout 

[http://ubuntuforums.org/showthread.php?t=1265224&page=5]("http://ubuntuforums.org/showthread.php?t=1265224&page=5")

---

### Post by ranch hand on 2009-09-14
You might want to try hitting the Esc key when the flasher starts.  I have had that behavior 3 times and twice that brought on verbose text.

Just a thought.

---

### Post by ljrmorgan on 2009-09-14
> **bwallum said:**
> Hi
I'm now using my **external drive** and jaunty to boot and diagnose. However, I think I need like some help to get the repair underway. Any offers please?

I'm running Karmic on AMD64, I get the same problem with the flashing cursor, but only when my USB hard drive is plugged in. Have you tried unplugging it and booting? That might fix it, and it'd be nice to know that I wasn't the only one having this problem.

---

### Post by bwallum on 2009-09-15
ljrmorgan - tried removing my usb hard drive - rebooted a couple of times - no change.
ranch hand - esc doesn't work for me. I can only do Alt SysRq reisub to get a reboot.
terry-gardener - changed nvidia to nv and then vesa in xorg.conf, rebooted a few times with each, no change. I am running nvidia 185 however so may try again if I get past the problem below.

I'm working on the other suggestions. This is the point at which the boot falls over:-

> 
.
.
.
[5.999424]ext3-fs: mounted filesystem with ordered data made
BEGIN: Running /scripts/local-bottom...
Done
Done
BEGIN: Running /scripts/init-bottom
Done

This is the point at which the kernel is fired up I think. So I checked the /boot directory and I do not have a linux image /boot/initrd.img-2.6.31-10-generic (which I think is karmic). 

However, I do have:

abi-2.6.31-10-generic
config-2.6.31-10-generic
System.map-2.6.31-10-generic
vmcoreinfo-2.6.31-10-generic
vmlinuz-2.6.31-10-generic

So it appears my upgrade failed to install /boot/initrd.img-2.6.31.10-generic and failed to write karmic to /boot/grub/menu.lst

Can I use the files I have to generate the kernel?

---

### Post by bwallum on 2009-09-16
My upgrade from 2.6.28.15-generic to 2.6.31-10-generic appears to have not completed. The screenshot shows lack of 'build' symbolic link and a volatile folder.

Any ideas on how to repair this?

---

### Post by bwallum on 2009-09-21
re-installed from alpha 6 cd...karmic up and running.

---

