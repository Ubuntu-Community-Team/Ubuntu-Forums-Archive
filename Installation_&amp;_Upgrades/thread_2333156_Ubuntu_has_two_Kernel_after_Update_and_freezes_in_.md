---
title: "Ubuntu has two Kernel after Update and freezes in booting"
date: 2016-08-07
forum: Installation &amp; Upgrades
---

### Post by reza.mrtz on 2016-08-07
I had a system software update message to install an update in Ubuntu(16.04). when I do that and reboot the system, 
Ubuntu freezes on booting with 5 dots. 
in Grub(2.02) menu when I open Advanced option,there is 2 Kernel! and this things appears:

Ubuntu, with Linux 4.4.0-31-generic
Ubuntu, with Linux 4.4.0-31-generic (upstart)
Ubuntu, with Linux 4.4.0-31-generic (recovery mode)
Ubuntu, with Linux 4.4.0-21-generic
Ubuntu, with Linux 4.4.0-21-generic (upstar)
Ubuntu, with Linux 4.4.0-21-generic (recovery mode)

and when I try to boot in option 1 or 4 this message shows up:
Loading Linux 4.4.0-31(or 21)-generic... 
Loading initial ramdisk...

Does any one knows how should I fix this, without reinstall the Ubuntu?

---

### Post by oldfred on 2016-08-07
Have you tried the recovery mode?

---

### Post by grahammechanical on 2016-08-07
It is normal practice not to remove an existing kernel when the system receives a newer kernel. This is done in case there is some kind of a conflict with the newer kernel. We can then access Advance options for Ubuntu and load an earlier kernel that may load without the problem we were having.

Also, the "loading initial ramdisk" is a normal thing to do. We should always have at least two kernels. At the moment I have 3 kernels and in the past I have had many more. When I run apt upgrade I see this.

> The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-32 linux-headers-4.4.0-32-generic
  linux-image-4.4.0-32-generic linux-image-extra-4.4.0-32-generic
Use 'sudo apt autoremove' to remove them.

If I run 'sudo apt autoremove' that  kernel will be removed but there will still be 2 newer kernels listed in the Advanced options sub-menu. My current kernel is 4.4.0-34. And I guess that the second kernel will be 4.4.0-33.

Regards

---

### Post by reza.mrtz on 2016-08-08
Yes I tried the recovery mode 3 or 4 times, not worked :(

---

### Post by oldfred on 2016-08-08
Was this a version update or just a regular update to parts of the current version you have installed?

Try removing quiet splash and see what posts. Often last thing posted is not the issue, but a few lines above is.
       At grub menu you can use e for edit, scroll to linux line and remove quiet splash.

Did you change video drivers, even if several days before you rebooted?
What video card/chip?

---

