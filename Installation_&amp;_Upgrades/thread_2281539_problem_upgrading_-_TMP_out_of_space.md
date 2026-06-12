---
title: "problem upgrading - TMP out of space"
date: 2015-06-07
forum: Installation &amp; Upgrades
---

### Post by NikosF on 2015-06-07
I was running ubuntu successfully (for mythtv) until I tried to upgrade.
Linux msi 3.16.0-37-generic #51-Ubuntu SMP Tue May 5 13:45:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

It appears I am out of space on my /tmp drive.  But - even cleaning it out doesn't seem to help:


I'm getting an error when I apt-get upgrade:
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
/usr/sbin/dkms: line 3056: cannot create temp file for here-document: No space left on device
/usr/sbin/dkms: line 424: echo: write error: No space left on device
/usr/sbin/dkms: line 424: echo: write error: No space left on device
/usr/sbin/dkms: line 424: echo: write error: No space left on device
/usr/sbin/dkms: line 424: echo: write error: No space left on device
/usr/sbin/dkms: line 424: echo: write error: No space left on device
/usr/sbin/dkms: line 424: echo: write error: No space left on device
/usr/sbin/dkms: line 424: echo: write error: No space left on device
/usr/sbin/dkms: line 424: echo: write error: No space left on device
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
Error! Bad conf file.
File: 
does not represent a valid dkms.conf file.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-34-generic
WARNING: missing /lib/modules/3.16.0-34-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.16.0-34-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/init’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/init’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./init-bottom/udev’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./init-bottom/udev’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./nfs’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./nfs’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./panic/console_setup’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./panic/console_setup’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./panic/keymap’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./panic/keymap’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./local’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./local’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./functions’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./functions’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./local-premount/resume’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./local-premount/resume’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./local-premount/ntfs_3g’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./local-premount/ntfs_3g’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./local-premount/fixrtc’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./local-premount/fixrtc’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./local-bottom/ntfs_3g’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./local-bottom/ntfs_3g’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./init-top/all_generic_ide’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./init-top/all_generic_ide’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./init-top/blacklist’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./init-top/blacklist’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/scripts/./init-top/udev’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/scripts/./init-top/udev’: No space left on device
sh: echo: I/O error
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/conf/initramfs.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/conf/initramfs.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//conf/conf.d/resume’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//conf/conf.d/resume’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//sbin/wait-for-root’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//sbin/wait-for-root’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libudev.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libudev.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libc.so.6’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libc.so.6’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libselinux.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libselinux.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/librt.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/librt.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//lib64/ld-linux-x86-64.so.2’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//lib64/ld-linux-x86-64.so.2’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libpcre.so.3’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libpcre.so.3’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libdl.so.2’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libdl.so.2’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libpthread.so.0’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libpthread.so.0’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//sbin/modprobe’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//sbin/modprobe’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//sbin/rmmod’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//sbin/rmmod’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/alsa-base.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/alsa-base.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-ath_pci.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-ath_pci.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-firewire.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-firewire.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-framebuffer.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-framebuffer.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-modem.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-modem.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-rare-network.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-rare-network.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-watchdog.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist-watchdog.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/blacklist.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/dkms.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/dkms.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/fbdev-blacklist.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/fbdev-blacklist.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/iwlwifi.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/iwlwifi.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/mlx4.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/mlx4.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/modesetting.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/modesetting.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/vmwgfx-fbdev.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk/etc/modprobe.d/vmwgfx-fbdev.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//sbin/blkid’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//sbin/blkid’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libblkid.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libblkid.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libuuid.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//lib/x86_64-linux-gnu/libuuid.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_ArwRDk//bin/date’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_ArwRDk//bin/date’: No space left on device
E: /usr/share/initramfs-tools/hooks/fixrtc failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.16.0-34-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.16.0-34-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-34-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by NikosF on 2015-06-07
nikos@msi:/$ df -h
Filesystem                 Size  Used Avail Use% Mounted on
/dev/sda1                  107G   32G   70G  32% /
none                       4.0K     0  4.0K   0% /sys/fs/cgroup
udev                       1.5G  4.0K  1.5G   1% /dev
tmpfs                      309M  1.1M  308M   1% /run
none                       5.0M  4.0K  5.0M   1% /run/lock
none                       1.6G   72K  1.6G   1% /run/shm
none                       100M   12K  100M   1% /run/user
overflow                   1.0M  1.0M     0 100% /tmp

---

### Post by papibe on 2015-06-07
Hi NikosF.

Could you post the output of these commands?
```
df -h

df -i

uname -a

dpkg -l | awk '/-headers-/ {print $2}'
```
Regards.

---

### Post by NikosF on 2015-06-07
Thanks: 

df -h:
```
Filesystem                 Size  Used Avail Use% Mounted on
/dev/sda1                  107G   32G   70G  32% /
none                       4.0K     0  4.0K   0% /sys/fs/cgroup
udev                       1.5G  4.0K  1.5G   1% /dev
tmpfs                      309M  1.1M  308M   1% /run
none                       5.0M  4.0K  5.0M   1% /run/lock
none                       1.6G   72K  1.6G   1% /run/shm
none                       100M   12K  100M   1% /run/user
overflow                   1.0M  1.0M     0 100% /tmp
```

df -i
```
Filesystem                   Inodes  IUsed     IFree IUse% Mounted on
/dev/sda1                   7118848 235913   6882935    4% /
none                         394784      4    394780    1% /sys/fs/cgroup
udev                         392007    522    391485    1% /dev
tmpfs                        394784    563    394221    1% /run
none                         394784      5    394779    1% /run/lock
none                         394784      3    394781    1% /run/shm
none                         394784     15    394769    1% /run/user
overflow                     394784    282    394502    1% /tmp
```

uname -a
```
Linux msi 3.16.0-37-generic #51-Ubuntu SMP Tue May 5 13:45:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

dpkg -l | awk '/-headers-/ {print $2}'
```
linux-headers-3.16.0-33
linux-headers-3.16.0-33-generic
linux-headers-3.16.0-36
linux-headers-3.16.0-36-generic
linux-headers-3.16.0-37
linux-headers-3.16.0-37-generic
linux-headers-3.16.0-38
linux-headers-3.16.0-38-generic
linux-headers-generic
```

---

### Post by papibe on 2015-06-07
Thanks.

/tmp is mounted as 'overflow'. This means that when the system boot, there was no space available and that was taken as a 'emergency' measure.

Since it looks like like you have made some space already, you should be able to unmount the partition:
```
sudo umount /tmp
```
or reboot in case the system does not allow you to do that live.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by NikosF on 2015-06-07
Thanks.

It won't let me unmount and there are a ton of processes using /tmp.  I can't kill all of them since I'm trying to debug over ssh

When you say there wasn't enough space on boot - are you talking memory or drive space?

---

### Post by papibe on 2015-06-07
Disk space.

Usually means no space to create temp files on /tmp directory, which most commonly is on the / partition.

There are 2 types of lack of space:
[LIST]
[*]Llack of actual space, that is, lack of available blocks to allocate the content of the files; or
[*]Lack of inodes, that is not able to create a file because there's no more space on the index table of the file system. The latter occurs because you have too many files (see [this]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1089195")).[/LIST]
Did it work, btw?

Regards.

---

### Post by NikosF on 2015-06-07
Thanks Papibe!

I rebooted (had to do recovery mode because I was getting a kernel panic) and there was no /tmp generated yet.  I couldn't unmounts since there wasn't a /tmp, but went ahead and did the apt-get upgrade and it worked this time.

Thanks for pointing me in the correct direction.

---

