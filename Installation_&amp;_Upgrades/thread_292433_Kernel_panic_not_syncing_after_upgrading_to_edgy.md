---
title: "Kernel panic: not syncing after upgrading to edgy"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by gctaylor1 on 2006-11-03
I upgraded from 6.06 xubuntu to 6.10 xubuntu last night and
have run into a problem booting now.  I followed the method
of apt-get dist-upgrade installation.

I get an error "Kernel panic - not syncing : VFS: Unable to
mount root fs on uknown-block(0,0)".

I've tried to fix it by chrooting into my native hard drive environment but I
can't seem to do it.  The details are that I ran the
xubuntu live-CD and then went into single-user mode and did
this:

# mkdir /mnt/hd
# mount /dev/hda1 /mnt/hd
# chroot /mnt/hda1 /bin/bash


# grub-install /dev/hda1
--root-directory=/mnt/hd/boot/grub/
The file /mnt/hd/boot/grub//boot/grub/stage2 not read
correctly.

After that failed I went to the grub prompt and
grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed
(this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed
(this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0)
/boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.



While I was looking around I noticed these new entries in my
fstab, does this have anything to do with it?
# cat /mnt/hd/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>
# <dump>  <pass>
proc            /proc           proc    defaults
0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=30377190-b126-4ce7-812e-b3d5f7a44732 / ext3
defa# /dev/hda5 -- converted during upgrade to edgy
UUID=de93726e-bc4d-4225-bfde-d3ee7eb65d4f none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto
0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=3791f311-075d-4313-9ceb-3c2b5823e08e /mnt/speedy10
reiserfs defaults 0 2


As you can see I have two drives, hda is my main OS drive,
hdb is used as my home directory. I only have xubuntu on the
hda drive.  I thought the problem might be because I have a
non-used Gentoo installation on hdb, and that might have
confused grub during the upgrade process somehow, but the
xubuntu on hda has been working and rebooting just fine over
the past few weeks without hdb getting in the way.  I've tried mounting the drive with ext2 and ext3 as I'm not sure right now what the correct fs is.

Does anyone have a clue becuase right now I'm confused?

---

### Post by picpak on 2006-11-03
*sigh* I hate this problem. Here's how I fixed it:

Boot into the live CD, open the terminal, and run:

```
mkdir /mnt/linux 
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc
sudo update-initramfs -u
```

---

### Post by gctaylor1 on 2006-11-04
Thanks picpac I thought you had it nailed but apparently I've run into another bug.  I get these errors:

--
root@ubuntu:/# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.15-26-386
cp: cannot stat `/etc/udev/rules.d/65-persistent-storage.rules': No such file or directory
cp: cannot stat `/etc/mdadm/mdadm.conf': No such file or directory
root@ubuntu:/#
--
I found the first error reported as Bug #60278 on launchpad.  I'm not that familiar with how this works but the bug says unconfirmed.  Does that mean it's waiting for a developer to confirm or another user, like me?

Question #2.  While I'm in the chroot environment is there anything I can do to either run the upgrade again or roll back to dapper so I can at least use my system?  

Thanks,
Gary

---

### Post by picpak on 2006-11-04
Are udev and mdadm installed? If not, while in chroot, run:

```
apt-get install udev mdadm
```

---

### Post by gctaylor1 on 2006-11-04
Yes, I believe udev and mdadm are installed based on this output:

```

# apt-get install udev mdadm
Reading package lists... Done
Building dependency tree
Reading state information... Done
udev is already the newest version.
mdadm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

I've also reinstalled initramfs-tools (and that seems to be working now) and then ran through your instructions again.  

I've also run 
```

dpkg --configure -a

```
because based on the bug I referenced, it seemed as though there were unconfigured packages.

I'm still getting the same initial error.

---

### Post by taistelutipu on 2007-11-30
wow, I didn't expect to find someone who has  exactly the same error output that I got. The only difference is that the upgrade is from 7.04 to 7.10 but the error is the same:

"Kernel panic - not syncing : VFS: Unable to mount root fs on uknown-block(0,0)".

You wrote something about "fix it by chrooting into my native hard drive environment but I
can't seem to do it."

What exactly does that mean? What is chrooting and the native hard drive environment?  And what do I have to do to abort the booting process ending in the error output above? I have no idea how I can get to the command prompt from there. The cursor just freezes after the error .:confused:

Thanks a lot in advance for your help
tipsku

---

