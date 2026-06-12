---
title: "grub - how to add to the boot process to a new disk with an old version of kubuntu?"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by emamm2008 on 2012-02-07
Hello

I have an almost exact image of /dev/sda on /dev/sdb. Since /dev/sda has been partially wrecked when attempting to upgrade to 11.04, I need to add /dev/sdb (and its kernels) to the boot options.

I read a howto on grub but I confess that I did not understand what I have to do.

Many thanks

Ed

---

### Post by oldfred on 2012-02-07
You say partially wrecked. Can you boot?

I like to have installs on different drives & install grub2's boot loader for that install to the MBR of the same drive. Then in BIOS I can change if I have issues with the one I normally boot.

You should be able to install grub to the sdb drive and boot that drive if it is a working install. Change sda to sdb in in example below. If not sdb5 change to your install. If separate /boot post back as you have to also mount that.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

This also may help:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by emamm2008 on 2012-02-13
Hello

Many thanks.  I did what you have suggested and kinda of work. If I remove one of the hds, the machine boots using the right kernel, but if I add the second one somehow the wrong kernel is used.  I have issued the commands given in your post several times (with and without the second hd) but the problem persists.

Cheers

Ed

---

### Post by oldfred on 2012-02-13
Did you do an image copy? That copies UUIDs and when you boot from UUIDs you do then know which of two duplicates it boots from.

Post boot info script from this.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

