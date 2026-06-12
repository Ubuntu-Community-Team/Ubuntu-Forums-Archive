---
title: "Upgrade from Jaunty to Karmic fails, unbootable"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by garvinhicking on 2009-12-08
Hi!

I've used the Wubi installer to put Ubuntu Jaunty on my Acer Aspire Revo, because without a CD-ROM and USB-Stick it was the easiest way to install Ubuntu onto the harddrive.

Now I've used the Ubuntu Upgrade to Karmic, and my system will not reboot. I get this message:

```

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/loop0
/tmp: waiting for (null)
/boot: waiting for /host/ubuntu/disks/boot
/media/DATA: waiting for /dev/sda3

```

this is my /etc/fstab:

```

proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw
/dev/sda3 /media/DATA ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

```

My /host mount shows me all the contents of my harddrive. "mount" returns this:

```

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs
proc on /proc type proc
sysfs on /sys type sysfs
varrun /on /var/run type tmpfs
varlock on /var/lock type tmpfs
udev on /dev type tmpfs
tmpfs on /dev/shm type tmpfs
devpts on /dev/pts type devpts
/dev/sda2 on /host type fuseblk
fusectl on /sys/fs/fuse/connections type fusectl
lrm on /lib/modules/2.6.28-12-generic/volatile type tmpfs
/host/ubuntu/disks/boot on /boot type none
/dev/sda3 on /media/DATA type fuseblk
securityfs on /sys/kernel/security
gvfs-fuse-daemon on /home/hornet/.gvfs type fuse.gvfs-fuse-daemon
tmpfs on /lib/modules/2.6.28-17-generic/volatile type tmpfs

```

Excuse possible typos, I needed to manually copy this. I figure that something is off with the way that karmic addresses the virtual partitions.

What can I do?

Thanks a heap,
Garvin

---

### Post by rich86 on 2009-12-20
you had any luck with this?

I have a very similar issue, in that it says it cannot activate the swap.

Thanks

---

### Post by garvinhicking on 2009-12-20
Hi!

After some more digging, it seemed as if my karmic upgrade rebooted in the middle of it, and thus many things were not done. Most importantly, the initrd was not built, and the new kernel was not entered into the bootloader (grub).

So what I did was to boot from a USB drive into a rescue ubuntu boot disk, did a chroot() and ran the apt upgrade, as well as rebuilt the initrd, and altered the wubi bootloader config to contain the new kernel.

So basically, I screwed up for interrupting the upgrade, but by continuing it from a rescue medium, all was recovered.

Maybe that helps in a way? I'm no expert, but if you have more questions I'd try to describe what I did :)

Regards,
Garvin

---

### Post by rich86 on 2009-12-21
Thanks for replying. I managed to chroot in and run an apt update and upgrade. umounted everything and then when i rebooted grub failed to work.

In the end i gave up and reinstalling wubi, next time i might just install ubuntu on a proper partition but its my parents laptop so i won't play too much...

Thanks for your help.

---

### Post by garvinrick4 on 2009-12-21
How can I access my Wubi install and repair my install if it won't boot?  
 

 Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:  
 

 sudo mkdir /win  
 sudo mount /dev/sda1 /win  
 

 Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein  
 

 sudo mkdir /vdisk  
 sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk  
 

 Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.  
 

 To check the filesystem you can use:  
 

 sudo fsck /win/ubuntu/disks/root.disk


Hope that helps  Garvinrick4   Oh bye the way nice name.

---

### Post by fiklein on 2010-02-14
There is a new GRUB bootloader. This page:  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
may help. Press Ctrl - F (control F) and type WUBI to highlight applicable sections. I liked WUBI, but have now gone to a native Linux partition as it seems more stable.

---

