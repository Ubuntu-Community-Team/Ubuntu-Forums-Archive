---
title: "Installing Linux in Linux (Lubi)"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by kagerato on 2011-03-12
The 'Lubi' project (see [http://lubi.sourceforge.net/lubi.html](http://lubi.sourceforge.net/lubi.html) ) performs essentially the task I seek, but it seems to be outdated (last updated in 2007).

In general, the idea is to install Ubuntu (or some other distribution) inside a file that resides on an existing partition.  That file itself contains a complete filesystem.

Though I made many a google search attempting to research the exact mechanism by which both Wubi and Lubi accomplish that goal, I was only able to ascertain a few things:

(1) No version of Grub has support for booting a filesystem-in-filesystem.  It can extract a few key files out of certain kinds of filesystems in order to start the kernel, but that's about the extent of its capacity.

(2) Therefore, the kernel to be booted itself needs to have the capacity to load a file as the root filesystem.

(3) The loop block device provides the essential capability to load a file as though it were a filesystem, and the abstraction is mostly to entirely transparent to the rest of the system.

(4) Almost the same effect can be achieved by loading a special kernel and initramfs that switches out the root filesystem with the desired one.  However, in this case the boot sequence is Grub -> Linux Minimal Subsystem -> Full Userspace .  It would be much more convenient to be able to control the system to be booted directly from grub, and not having any special init scripts to select and/or swap the root filesystem.

I imagine there must be someone out there who has done this and understands the underlying mechanisms very well.  The closest I've come to a concrete example of it, however, are sample grub configurations for Wubi.  Those look like this:

```

menuentry "Ubuntu, Linux 2.6.31-14-generic"
{
  insmod ntfs
  set root='(hd0,1)'
  
  search --no-floppy --fs-uuid --set be4c68fe4c68b337
  
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
  
  linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
  initrd /boot/initrd.img-2.6.31-14-generic
}

```

My key questions are these:

(1) Does this mechanism require a special kernel?  It doesn't look like it, but I can't be sure.  Some of the Lubi packages seem to ship a precompiled kernel, but that might only be for convenience rather than necessity.

(2) Where is this loop= kernel option documented?  I can't seem to find official kernel documentation on this.  Several documents record a "max_loop" parameter, but no loop.  My sneaking suspicion is that this may not be an offical core parameter, but something used by the initial ramdisk.

(3) Does this mechanism require a full disk or full partition in the disk image, or will it work loading just a straight filesystem?  This is really only of concern for simplicity reasons, since I see no reason to complicate matters unnecessarily.

If anyone wonders why I would want to use this mechanism, it has certain advantages for backups and testing/experimentation.  One, it's much faster than virtualization, since the only performance overhead is passing through the top-level filesystem.  Two, maintaining many separate partitions is a hassle, especially when one realizes the sizes are wrong or there are not enough entries in the existing partition table.  Creating and deleting filesystem images is simpler and more self-contained, by comparison.

Oh, and I'm aware that btrfs provides essentially exactly the capability I'm looking for as "subvolumes".  I have concerns about the stability/reliability of that filesystem, though, since it still seems to be under heavy development.

---

### Post by bcbc on 2011-03-12
[https://launchpad.net/lupin](https://launchpad.net/lupin)

---

### Post by kagerato on 2011-03-12
If I'm understanding the Lupin page correctly, it appears to work using an initial ram filesystem and a special boot script.

Did I miss anything there?  I may have to resign myself to that approach if there is no other straightforward method.

---

### Post by bcbc on 2011-03-12
I haven't created a loop install from scratch. I tend to focus on the reverse: turning a loop install into a regular one.

If you aren't using the 'traditional' method which involves running ubiquity to install it, you'll need to copy your install to the loop device, chroot in to install lupin and regenerate the initrd, and then you need a mechanism to boot it. Grub2 can loop mount it and boot the kernel direct as shown in the boot script you have in your first post. With grub legacy I don't think it had this ability and required the kernel and initrd outside of the loop device.

As far as I know, lupin wasn't compatible with all linux versions - so you are probably limited by that in terms of the distributions you can use.

Good luck

---

### Post by kagerato on 2011-03-13
Understood.  Thanks for your help; that takes the mystery out of the mechanism.

---

