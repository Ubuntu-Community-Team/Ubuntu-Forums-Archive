---
title: "Preseed LVM PV's on whole (unpartitioned) disks"
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by jmccanta on 2016-01-24
I am trying to figure out how to install ubuntu, via preseed file, that will build a system that has LVM PV's created on whole (unpartitioned) disks, e.g., /dev/sdb, /dev/sdc. This is for a virtual environment (VMware).  Having the PVs on whole disks allow the disk to be grown and filesystem to be grown without reboot. I know we can add drives after the fact, but our preferences are to have a volume exist on a single PV. 

I have a script that partman/early_command can run that does the pvcreates, vgcreates, lvcreates and mkfs and mounts them in /target, if needed.

I am looking for a solution that will either (a) tell partman to use /target as it's laid out or (b) tell partman to use existing volume groups without creating PV's.
I've nearly got (a) to work by using a partman-auto/method of 'regular' and providing a recipied for /boot. However, none of the LVM parts are built into the initramfs.
(b) seems like a bug that Debian isn't going to fix.
I am open to other ideas for how to do this, including hacks.  The system boots over the network with DHCP. I can download pkgs/scripts to it.  
The solution needs to work with Precise/Trusty/Xenial.

Thanks.

---

