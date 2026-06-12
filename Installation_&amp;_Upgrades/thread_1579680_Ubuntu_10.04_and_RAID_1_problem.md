---
title: "Ubuntu 10.04 and RAID 1 problem"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by Cvieri on 2010-09-22
There is an experience in RAID 1 and UBUNTU 9.04. Decided to create RAID on Ubuntu 10.

After the set up appears the following:    

```
mount: mounting /dev/disk/by-uuid/XXXXXXXXXXXXXXXXXXXXXXXXXX on /root
failed: invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory.
mount: mounting /sys on /root/sys failed: No such file or directory.
mount: mounting /proc on /root/proc failed: No such file or directory.
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
BusyBox v1.13.3...
```Once again was trying to delete partitions and creating a new partition table with the gparted. And also to zero superblocks through mdadm --zero-superblock /dev/sdX. The same situation.

Any help?

---

### Post by Cvieri on 2010-09-22
Does nobody face this problem?

---

### Post by dspratomo on 2011-01-02
I just did the same, I have experience RAID5 with Ubuntu 8.04, however when I tried Ubuntu 10.04 with RAID1, I face the same problem with yours, this is the first answer google get me

---

### Post by flexy75 on 2011-01-03
I have a 4 disk setup, with root set up at raid1 with 4 disks. Other partitions are raid5 partitions used with media files. I mucked around with the PC and accidently got one SATA cable loose. Did not notice it, closed the case and powered it on. First the system booted up with degraded raid partitions. I noticed it and shut down the system, found the loose cable... Plugged it properly in and booted. This time I got the exact same errors as the starter of this thread. Grub is installed on every disks MBR, it refers to root by UUID, which is md device.

The question is, why the system failed to assemble the root raid device and mount it?

And is it possible to define non root raid devices so that if they are degraded on boot, but was fine at last shutdown (which was proper shutdown), they do not assemble without a user input? This is because they were assembled degraded at the first boot and because of that it takes 20-40h to run the recovery. I could use `sysctl -w dev.raid.speed_limit_min=50000` or alike to speed rebuilding redundancy on the raid5 devices, but that takes too much from the system, the main use of the computer suffers way too much.

---

### Post by techexpert on 2011-03-22
Same here, trying to install RAID1 with mdadm by using the "alternate" installation CD and after everything goes through and the computer reboots, I am getting the same message. Has anyone been able to find a solution?

---

### Post by deconstrained on 2011-03-22
Recent posters: is this software RAID or hardware RAID being discussed here? There's a very, VERY big difference.

I've never really installed Ubuntu from scratch onto a software RAID (mdadm) using the automatic stuff, because configuring it after moving it to a RAID from a backup copy is pretty straightforward (and it's also easier to control/configure the disk geometry for better performance that way). But a few things that are easy to forget are:

- Use the --modules="raid" option with grub-install 
- Add the appropriate modules for whatever "flavors" of RAID you're using to /etc/initramfs-tools/modules
- Have all the arrays you want running at boot time in /etc/mdadm/mdadm.conf ('mdadm --detail --scan' gives you output appropriate for putting in there if you assemble when booted to a livedisk)

If you take care of those three things and correctly configure your /etc/fstab, mkinitramfs should do everything necessary so that Ubuntu can boot properly.

---

