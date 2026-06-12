---
title: "Live USB: Can't take casper snapshot"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by DarkMorford on 2012-10-29
I'm trying to set up a 12.04.1 Live environment with persistence on my flash drive. I can boot into the system without any problem, but I haven't been able to use casper-snapshot to set up the persistence file.

According to the manpage, casper-snapshot pulls from /cow by default. However, I can't access /cow to take a snapshot of it. If I look at /proc/mounts, I can clearly see that there is a tmpfs filesystem mounted at /cow. But /cow is then mounted at / as part of an overlayfs setup, so it's not accessible in the root filesystem.
```
rootfs / rootfs rw 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=1987088k,nr_inodes=208218,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,relatime,size=797904k,mode=755 0 0
/dev/sdc2 /cdrom ext3 ro,noatime,errors=continue,user_xattr,acl,barrier=1,data=ordered 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /cow tmpfs rw,noatime,mode=755 0 0
/cow / overlayfs rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0
/dev/sdc1 /media/SMORFORD vfat rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro 0 0

```How can I get at the /cow tmpfs in order to make a snapshot?

---

### Post by C.S.Cameron on 2012-10-29
Why do you want to set up the persistence file, (casper-rw)?
Everything works good for me using UNetbootin or Startup Disk Creator out of the box.

You can mount cassper-rw to access files using:

```
sudo mkdir /media/casper
```

```
sudo mount -o loop casper-rw /media/casper/
```

---

### Post by DarkMorford on 2012-10-29
I'm trying to create a [FONT=Courier New]casper-sn[/FONT] file that gets loaded at boot time and updated at shutdown. My understanding is that this will result in fewer writes to my flash drive than having a [FONT=Courier New]casper-rw[/FONT] file or partition.

---

### Post by C.S.Cameron on 2012-10-29
Changing the name of a blank casper-rw file to casper-home makes a persistence file for home.

I wonder if just changing the name of a blank casper-rw file to casper-sn will give what you want?

This sounds like a good idea and would like to know how to make a drive with limited writes but I'm not too concerned about bricking a decent flash drive running Ubuntu, it would take years at 20MB/s write speed.

Please let us know what works.

---

### Post by funicorn on 2012-10-30
Why bother ? Just use **universal installer** in windows which can install a live system with persistence in a couple of minutes.

---

### Post by DarkMorford on 2012-10-31
I'm trying to avoid using an installer package because I've already got a bootloader installed on this flash drive with memtest86+ and GParted, as well as a bunch of data files I need for my classes. And as I said, I can boot into Ubuntu fine, it's just the persistence that's giving me trouble.

> Changing the name of a blank casper-rw file to casper-home makes a persistence file for home.

I wonder if just changing the name of a blank casper-rw file to casper-sn will give what you want?This sort of worked. I actually started by created a regular casper-rw file so I could get some data (settings and such) in there, then renamed it to casper-sn after rebooting into non-persistent mode. When I started with persistent again, Ubuntu loaded the snapshot fine, but didn't update it when I shut down. As before, the error message indicated that it couldn't find /cow to make the snapshot from.

I started looking through the scripts in initrd.lz for the function that overlays /cow onto the root; I wanted to add a bind-mount so I could see it after the boot had finished. Turns out there's already a function to do that—adding either [FONT=Courier New]showmounts[/FONT] or [FONT=Courier New]show-cow[/FONT] to the kernel command line (they're synonymous) causes it to create that mount point. All of a sudden [FONT=Courier New]casper-snapshot[/FONT] does exactly what it should. Almost.

From reading the casper init scripts, it seems that it only respects the [FONT=Courier New]persistent-path=[/FONT] parameter with regard to the [FONT=Courier New]casper-rw[/FONT] and [FONT=Courier New]home-rw[/FONT] files. That is, it won't load snapshots unless they're in the flash drive's root directory. This is something I'd like to fix, owing to the way I use this flash drive. Modifying these scripts and repacking them into an initrd is simple enough, but my concern is what happens when a kernel update comes along and needs to call update-initramfs. (update-initramfs isn't working right now either, but that's a topic for another thread.) When the system rebuilds its initrd, how can I make sure my script changes propagate?

---

