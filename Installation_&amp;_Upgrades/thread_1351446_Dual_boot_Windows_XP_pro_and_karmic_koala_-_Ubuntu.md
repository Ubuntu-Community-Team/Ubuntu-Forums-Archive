---
title: "Dual boot Windows XP pro and karmic koala - Ubuntu won't boot"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by anne_so on 2009-12-10
Hi, 

I have Windows XP pro on my computer and tried to install Karmic Koala to another partition. The installation seemed to work fine, and I get a grub menu when I boot. From the menu, the windows option works well, but choosing Ubuntu gives the following error:

udevadm trigger is not premitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
svgalib: Cannot open /dev/mem.
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough)
  -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/9efc30fd-c539-4b3c-a1f6-3f98bb222fb9 does not exist.
Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

Somebody suggested that the problem might be with the UUID, and we tried solutions in that sense but nothing worked. Could it be a problem with udev? How do I fix that? Any help would be greatly appreciated!

Anne-Sophie

---

### Post by ecowan on 2010-02-02
Me too.
I installed karmic from a cd (which worked on another machine onto my Sony Vaio, formatting the disk except for a Windows XP partition. Everything seemed to go alright. Once I had rebooted I asked Synaptic to upgrade all packages. That too seemed to work.

Now when I boot I get these same messages on a terminal screen.

If I pick ...17 (recovery mode) from the grub menu I get the same.

If I pick ...14 from the grub menu it gives me the new splash screen for a moment, but only in the top left 3/4 of the screen. I get a chance to login. The desktop comes up and works, except that I get a 3/4 screen.

I fire up synaptic again, who tells me to run dpkg --configure -a.
That runs, apparently completing the creation of the /boot/initrd.img...

I reboot. ...17 gets to login screen. Screen is still 3/4. But desktop never comes up. I get a full screen of what looks like an over-exposed photograph with lots of flickering in the hard-disk lde for a couple of minutes. Then just the fuzzy blank screen.

- Erny

---

