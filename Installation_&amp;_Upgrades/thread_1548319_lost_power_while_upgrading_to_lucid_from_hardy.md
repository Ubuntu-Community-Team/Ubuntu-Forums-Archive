---
title: "lost power while upgrading to lucid from hardy"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by bhram on 2010-08-08
Hi,

I tried to upgrade my kubuntu 8.04 LTS to Ubuntu 10.04 LTS as given [here]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade"). Actually I wanted to upgrade to kubuntu. The download completed successfully. However,while upgrading the power went off and left the computer in bad state. Now I see multiple two entries for both 
kubuntu 8.04.4 LTS, Kernel 2.6.24-28-generic
kubuntu 8.04.4 LTS, Kernel 2.6.24-28-generic (recovery mode)
in grub. Since I am not that familiar with ubuntu(in general linux), I would like you to help me to come out of this problem.
When I tried to boot in first two of these I get the following error message and it remains in command-line mode.
```

libudev: udev_monitor_new_from_netlink: error getting  socket: Invalid argument
[   20.839013] wait-for-root[946]: segfault at 00000030 eip b774bf2b esp bfb33340 error 4
Segmentation fault
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
   - Check rootdelay = (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/by-uuid/a065b113-da11-492f-945c-5d0a33b96cc9 does not exist. Dropping to a shell!

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) build-in-shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) cat /proc/cmdline
root=UUID=a065b113-da11-492f-945c-5d0a33b96cc9 ro single
(initramfs) cat /proc/modules
fuse 50708 1 - Live 0xf8830000
(initramfs) ls /dev
console    pts     tty2    tty4      tty6
null          tty1    tty3    tty5

```When I tried the later two entries in grub, I get the following error:

```

libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
mountall: mountall.c:3204: Assertion failed in main: udev_monitor = udev_monitor_new_from_netlink (udev, "udev")
init: mountall main process (2777) killed by ABRT signal
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
Give root password for maintenance
(or type Control-D to continue):

```in recovery mode after getting above error
```

root@(none):~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:     Ubuntu 10.04.1 LTS
Release:         10.04
Codename:     lucid
root@(none):~# df -h
(shows multiple line output with /dev/... entries and their mount points. However, the mount points are not having anything. It is like nothing got mounted.

```Can anyone help to recover from this? I would suspect there should be some way where I should be able to locate the downloaded upgrade stuff and apply it afresh again from start. Is this something possible?

Regards

---

### Post by bhram on 2010-08-08
I thought this might be something that must have been faced by some others too and someone can help me ... :-(. Well, it would be good if someone can at least tell me that the recovery is possible or should I do a fresh install of hardy before trying to upgrade again?

-Bhram

---

### Post by dino99 on 2010-08-08
youd better to install again from scratch

prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by oldfred on 2010-08-08
Reinstall may be the best solution, if you have all your data backed up and know all the programs you have installed. But you can try this:

If you can log into a terminal, do you have network access? If so you can run these commands. If not you can chroot into your system from a liveCD and run these commands.

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc

Chroot:
kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

---

### Post by bhram on 2010-08-14
Thanks Guys for your help. I decided to reinstall it today. However, I am still facing a problem. I will start a separate for that problem as this topic will be confusing then.

---

