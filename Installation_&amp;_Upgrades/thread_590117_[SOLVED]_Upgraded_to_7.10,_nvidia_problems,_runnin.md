---
title: "[SOLVED] Upgraded to 7.10, nvidia problems, running wrong kernel?"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by RedPill on 2007-10-24
I've been running both 32 bit and 64 bit 7.04 Unbuntu with the nvidia restricted drivers on a Dell Dimension 9200 with a Core 2 Duo processor and the nvidia 7300LE without any problems since March.

I just upgraded to 7.10 last Friday (should have waited!!!), and have since been unable to get X working with my nvidia 7300 LE card.

The machine has many boot options: 32-bit Ubuntu, 64-bit Ubuntu, Vista.  I only upgraded the 64-bit partition (thankfully), but that was the main boot configuration I was using.

I have tried many of the recipes posted on this forum to try and get the nvidia video card to work properly, but none have worked (this includes trying envy).

If I try to use envy or installing nvidia driver directly, the process always stops and complains that the kernel sources can't be found.  The one time I got past this problem by using -kernel-sources option, the resulting driver wouldn't load.

Now I'm wondering if grub might be part of the problem.  Since I used the Upgrade Option to install 7.10 (7.04 -> 7.10), there are no new boot options - so I'm still selecting the 'Ubuntu, kernel 2.6.20-16-generic 64 bit' boot option from grub.

If I cat /etc/issue, I get:

Ubuntu 7.10 \n \l

If I enter uname -r, I get:

2.6.20-16-generic

Is that a proper combination?  Shouldn't uname -r give me:

2.6.22-14-generic

Is the 2.6.22-14-generic kernel on my system, but just hiding somewhere?  Can I fix grub to load it instead?

Any ideas???

I've been a big fan of Ubuntu up til now, but my enthusiasm has faded subtantially - I've burned way too much time on this.

---

### Post by RedPill on 2007-10-24
OK, this is interesting.

If I look in /boot/menu.lst on the 64-bit partition, I see a bunch of new options THAT I DON"T SEE WHEN I BOOT:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=<cut> ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=<cut> ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=<cut> ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=<cut> ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

So it seems that the automatic upgrade process doesn't handle multi-boot situations very well - it modified grub's menu.lst, but NOT the one on the boot partition.

Off to try and add one of these options to the menu.lst on the boot partition.

*@%(@%

---

### Post by RedPill on 2007-10-24
I'm pretty sure these problems are related to using the automatic upgrade process in a multi-boot environment.

I've started a thread on that topic:  [http://ubuntuforums.org/showthread.php?t=590174]("http://ubuntuforums.org/showthread.php?t=590174")

---

### Post by pbcartwright on 2007-10-24
I have that nvidia card also, and I have 2 DELL desktop boxes with NVIDIA cards. 
I would suggest you install envy and let it configure your graphics..
to get X working first, if you edit /etc/X11/xorg.conf and change the driver from "nvidia" to "nv" you can at least start X and get ubuntu/Kubuntu working..

---

### Post by RedPill on 2007-10-24
pbcartwright, thanks for your reply.

Unfortunately, as I mentioned, envy wasn't working for me, nor were any of the other recipes.

The root of my problem was a combination of a multi-boot configuration and the automatic upgrade process.

I booted to my 64-bit configuration on partition [hd0,4] and then did the automatic upgrade from 7.04 (feisty) to 7.10 (gutsy).

Once I was done, I was unable to get X to work with my nvidia 7300LE card, and none of the recipes to fix the problem worked.

The reason was that the automatic upgrade process did not update grub's menu.lst on my boot partition, which is on [hd0,7].  The upgrade process instead updated grub's menu.lst on [hd0,4].

Therefore, when I booted, I was selecting an (outdated) entry from [hd0,7] menu.lst that loaded the wrong kernel (2.6.20-16-generic, rather than 2.6.22-14-generic).

I copied an entry from menu.lst on [hd0,4] to the menu.lst [hd0,7], rebooted, and selected the newly-added option.  At that point, the information contained in thread [http://ubuntuforums.org/showthread.php?t=581119&highlight=nvidia&page=3]("http://ubuntuforums.org/showthread.php?t=581119&highlight=nvidia&page=3")
worked perfectly to get the nvidia card working.  From that thread:

sudo nano /etc/default/linux-restricted-modules-common

Make the last line look like
Code:

DISABLED_MODULES="nv nvidia nvidia_legacy"

ctrl+x and y to save.

Then all this in a Terminal no X

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start

---

