---
title: "XBMCbuntu - on kernel update run into &quot;no space left on device&quot;"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by VictorR on 2013-06-21
On XBMCbuntu (which is Lubuntu + XBMC) on routine updates suddenly run into kernel configuration problems. Ended up with the message suggesting to run "dpkg --configure -a". This now always fails with following output:
```

victor@XBMC:~$ sudo dpkg --configure -a
[sudo] password for victor: 
Setting up linux-image-3.5.0-34-generic (3.5.0-34.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.5.0-34-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-34-generic
cp: cannot create regular file `/tmp/mkinitramfs_BzOKvb//lib/firmware/radeon/TURKS_me.bin': No space left on device
cp: cannot create regular file `/tmp/mkinitramfs_BzOKvb//lib/firmware/radeon/TURKS_pfp.bin': No space left on device
cp: cannot create regular file `/tmp/mkinitramfs_BzOKvb//lib/firmware/radeon/BTC_rlc.bin': No space left on device
....
many similar lines below, and eventually...

cp: cannot create regular file `/tmp/mkinitramfs_BzOKvb//sbin/mount.fuse': No space left on device
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.5.0-34-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-34-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-34-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-34-generic; however:
  Package linux-image-3.5.0-34-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.5.0-34 (3.5.0-34.55) ...
dpkg: unrecoverable fatal error, aborting:
 unable to create `/var/lib/dpkg/updates/tmp.i': No space left on device

```
Free space check gives:
```

 df -m
Filesystem     1M-blocks   Used Available Use% Mounted on
/dev/sda3           5686   4548       850  85% /
udev                 993      1       993   1% /dev
tmpfs                402      1       401   1% /run
none                   5      0         5   0% /run/lock
none                1004      0      1004   0% /run/shm
none                 100      0       100   0% /run/user
/dev/sdb1        1907726 320159   1587568  17% /media/ntfs
/dev/sda1         227167   9384    206243   5% /home

```
other disk space checks return matching 850MB, which must be pretty much enough for updates.

What I have noticed the lines like:
cp: cannot create regular file `/tmp/mkinitramfs_BzOKvb_**//**_lib/firmware/radeon/BTC_rlc.bin': No space left on device
have double slashes(?)

What to do next?
Any ideas would be greatly appreciated.

Thanks!

---

### Post by marinara on 2013-06-21
i agree with you, 850MB should be plenty of space, but if you really have no other ideas, i would get more disk space.

---

### Post by VictorR on 2013-06-22
I just wonder, if there is anything I could delete and start update process all over again. Currently neither apt-get nor dpkg work, referring to each other as the source of problem. fsck did not reveal any problems. And I don't believe that 850 MB of free space after all packages were dowloaded (about 60 MB) is really "no space left". There is something elese is broken, but I cannot figure out what, and how to overtake this. I am not familiar with the installation process in depth and what I'd like to know is, how to force it to ignore, what was partially made and start from the beginning.

Can anybody help me?

---

### Post by shorty123 on 2013-06-25
Try to purge all the unused linux kernel headers: [http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/](http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/)

Worked for me.

The problem ist that you have additional boot partition (which is only around 200mb big) which is probably full with unused kernel headers.

---

