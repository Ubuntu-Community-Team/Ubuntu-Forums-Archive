---
title: "grub - jaunty boots from b0rked karmic partition"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by itzfritz on 2009-10-02
I (unsuccessfully) installed the karmic alpha5 on a spare partition on the drive that jaunty is installed.  This left me with an mbr that points to karmic's grub (2) bootloader, from which there was no option to boot jaunty.
I hacked it working by editing karmic's grub.conf to point to the jaunty kernel (from a livecd). 
boot --> karmic grub.conf --> jaunty kernel/initrd

I would like to know simply how to fix the mbr to point to jaunty's grub (1) bootloader, so that I can try out the karmic beta without having to go through this again.

Thanks!

---

### Post by oldfred on 2009-10-02
When I installed Karmic I knew I did not want it to take over boot, so I installed the boot to the partition not the MBR and then chainbooted from my Jaunty. On updates to Karmic I am getting warnings that having it in a partition uses blocklist and that is not recommended, but it works for me.

You just need to reinstall Grub and tell it to point to your Jaunty install.

If you can get into your install:

Quick Re-Install GRUB, if file locations are known
4-step short story

In terminal
  sudo grub
  root (hd0,x)    <-- this must point to location of 'stage1', else see nb:
  setup (hd0)     <-- installs grub IPL to MBR of first hard drive. 
  quit

Reboot

nb: if location of 'stage1' is unknown,
  find grub/stage1
or
  find /boot/grub/stage1

---

