---
title: "[SOLVED] WARNING: auto upgrade 7.04 -&amp;gt; 7.10 didn't update grub's menu.lst on boot par"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by RedPill on 2007-10-24
Please also see my first post related to this topic:

[http://ubuntuforums.org/showthread.php?t=590117]("http://ubuntuforums.org/showthread.php?t=590117")

I have a multi-boot installation that allows me to boot 32-bit and 64-bit Ubuntu, along with Vista.

I booted to my 64 bit partition, and then upgraded.  The upgrade process updated grub's menu.lst on THAT partition, but not on my boot partition.

Therefore, when I was booting back to the 64-bit partition using the menu.lst on the boot partition, THE WRONG KERNEL VERSION was being loaded.

This caused all sorts of problems, chief being that I couldn't get the nvidia drivers to work, and the recipes for fixing it wouldn't work either.

***If you have a multi-boot installation, be very careful using the automatic upgrade or use a different upgrade approach.***

Disclaimer: I am not an Ubuntu/Linux expert, so it's still possible I've misdiagnosed the source of my problems.

---

### Post by dougfractal on 2007-10-24
Hi RedPill

I don't know you partionsetup 
> If I look in /boot/menu.lst on the 64-bit partition, I see a bunch of new options THAT I DON"T SEE WHEN I BOOT:

but I guess your grub is reading from your  32 bit partition.  

method one:   merge  64-bit partition://boot/menu.lst  with 32-bit partition://boot/menu.lst

method two
grub   { follow a grub guide for ubuntu }  (sorry not to helpful but it's late ;-)

---

### Post by RedPill on 2007-10-24
dougfractal, thank you for your kind reply.

You are correct, that was the source of my problem.

The root of my problem was a combination of a multi-boot configuration and the automatic upgrade process.

I booted to my 64-bit configuration on partition [hd0,4] and then did the automatic upgrade from 7.04 (feisty) to 7.10 (gutsy).

Once I was done, I was unable to get X to work with my nvidia 7300LE card, and none of the recipes to fix the problem worked.

The reason was that the automatic upgrade process did not update grub's menu.lst on my boot partition, which is on [hd0,7]. The upgrade process instead updated grub's menu.lst on [hd0,4].

Therefore, when I booted, I was selecting an (outdated) entry from [hd0,7] menu.lst that loaded the wrong kernel (2.6.20-16-generic, rather than 2.6.22-14-generic).

I copied an entry from menu.lst on [hd0,4] to the menu.lst [hd0,7], rebooted, and selected the newly-added option. At that point, the information contained in thread [http://ubuntuforums.org/showthread.php?t=581119&highlight=nvidia&page=3]("http://ubuntuforums.org/showthread.php?t=581119&highlight=nvidia&page=3")
worked perfectly.

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

### Post by dougfractal on 2007-10-25
I'm surprised that nvidia-glx-new doesn't work for your card.


there is a sym link /vmlinuz and /intrid.img  that points to the last kernel install in the /boot/  if you use this in your menu.lst your booting will always be upto-date.   keep a copy of the old menu.lst as an error could make your computer unbootable.

---

