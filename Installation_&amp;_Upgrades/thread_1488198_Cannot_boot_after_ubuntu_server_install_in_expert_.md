---
title: "Cannot boot after ubuntu server install in expert mode"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by meglio on 2010-05-19
1. I have 4 HDD drives x 1TB.

2. My goal: I want to have /boot partition outside
raid and everything else on raid (except swap)

3. On first drive I have partition 300mb,
mountpoint=/boot, flag=bootable

4. Everything else I have in software RAID10 (with LVM over it).

4.1. I have logical partition over my raid,
mountpoint=/ (root)

5. My mother only supports fake raid, so I decided to not use it at all. I decided to use software rade.

6. I burn Ubuntu Server 10.04 DVD and booted from it and started installation in expert mode.

7. I partioned everything manually.

8. I selected GRUB when it asked to select what bootloader to use.

9. I then finished installation, rebooted and it wan't boot.

10. Finally I booted from my Ubuntu Live CD and collected some info by boot info script:
[http://pastie.org/private/hsf14imssprmwsemteysug](http://pastie.org/private/hsf14imssprmwsemteysug)


11. I do not know what to do next...
11.1. Is the problem is with grub?
11.2. Do I still have my ubuntu server installation unbreaked?
11.3. How to fix finally fix this problem that I'm trying to solve in 30-hours-non-stop-mode.


Thank you very much in advance,
Anton

---

### Post by meglio on 2010-05-19
P.S. I have IPMI (KVM over LAN) with static IP, so it's accessible from outside. Just in case someone will want to try...

---

### Post by meglio on 2010-05-20
Anyone can help?

---

### Post by meglio on 2010-05-23
Can anyone help me with this problem please?

---

### Post by dino99 on 2010-05-23
maybe some help:

[http://ubuntuforums.org/showthread.php?t=1474950](http://ubuntuforums.org/showthread.php?t=1474950)
[https://bugs.launchpad.net/initramfs-tools/+bug/570084](https://bugs.launchpad.net/initramfs-tools/+bug/570084)
[http://aplawrence.com/Linux/rebuildraid.html](http://aplawrence.com/Linux/rebuildraid.html)
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)
[http://neildecapia.wordpress.com/2010/05/15/ubuntu-lucid-10-04-on-a-raid-0%C2%A0array/](http://neildecapia.wordpress.com/2010/05/15/ubuntu-lucid-10-04-on-a-raid-0%C2%A0array/)
[http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html](http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html)

---

### Post by oldfred on 2010-05-23
You are using old grub, new grub is better with raid I think. The script does not parse raid systems well as raid is not common on desktops.

Your sda does not show the install and I would expect the script to see it if it is not part of the raid set. Are the /boot & /boot/grub files all there?

---

