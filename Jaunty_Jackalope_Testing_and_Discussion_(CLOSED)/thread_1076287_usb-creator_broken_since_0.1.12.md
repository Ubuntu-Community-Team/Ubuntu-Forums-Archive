---
title: "usb-creator broken since 0.1.12?"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-02-21
I have tested with 3 different and properly formatted USB sticks as well as 3 different dailies/alpha isos.

All of them fail at around 70% while installing the liveusb environment to the stick.

Manually downgrading to 0.1.11 or 0.1.10 fixes the problem.

Anyone else experiencing this?

---

### Post by Starks on 2009-02-22
bump.

---

### Post by ormandj on 2009-02-23
Same problem (I think). I get a window with a red minus icon when it fails, but no error message. Haven't run it from cli w/ strace to diagnose yet, but it sounds like you're encountering the same thing.

---

### Post by taavikko on 2009-02-23
> **ormandj said:**
> Same problem (I think). I get a window with a red minus icon when it fails, but no error message. Haven't run it from cli w/ strace to diagnose yet, but it sounds like you're encountering the same thing.

Just tested. usb-creator runs bit funny (no info available/progress)
fails around 80% just an educated guess since no visible progress%

```
-- Starting up at 08:41:22 --
[08:41:22] adding: /dev/sdc
[08:41:32] mounting /home/devil/Public/jaunty-desktop-i386.iso
[08:41:32] ['mount', '-t', 'iso9660', '-o', 'loop,ro', '/home/devil/Public/jaunty-desktop-i386.iso', '/tmp/tmpnW50NH']
[08:41:32] updating dest_status as part of update_row_state
[08:41:32] ['umount', '/tmp/tmpnW50NH']
[08:41:32] ['rmdir', '/tmp/tmpnW50NH']
[08:41:35] ['umount', '/dev/sdc1']
umount: /dev/sdc1: not mounted
[08:41:35] ['umount', '/dev/sdc']
umount: /dev/sdc: not mounted
[08:41:35] ['parted', '-s', '/dev/sdc', 'mklabel', 'msdos']
[08:41:35] ['parted', '-s', '/dev/sdc', 'mkpartfs', 'primary', 'fat32', '0', '--', '-0']
[08:41:37] deleting /dev/sdc from the ui
[08:41:37] device removed and none left.  source = False
[08:41:37] possibly adding: /org/freedesktop/Hal/devices/volume_uuid_53D2_F3C7
[08:41:37] new device:
{'capacity': dbus.UInt64(1031798272L), 'uuid': '53D2-F3C7', 'label': '', 'free': 0, 'fstype': 'vfat', 'device': '/dev/sdc1', 'mountpoint': '', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_53D2_F3C7'}
[08:41:37] adding: /dev/sdc1
[08:41:37] updating dest_status as part of update_row_state
[08:41:38] updating dest_status as part of update_row_state
[08:41:38] prop modified
[08:41:38] device_udi: /org/freedesktop/Hal/devices/volume_uuid_53D2_F3C7
[08:41:38] num_changes: 2
[08:41:38] change: volume.mount_point
[08:41:38] change: volume.is_mounted
[08:41:50] Installing...
[08:41:50] Source CD: /home/devil/Public/jaunty-desktop-i386.iso
[08:41:50] Destination disk: /dev/sdc1
[08:41:50] Persistence size: 134217728 MB
[08:41:50] Marking partition 1 as active.
[08:41:50] installing the bootloader to /dev/sdc.
[08:41:50] ['dd', 'if=/usr/lib/syslinux/mbr.bin', u'of=/dev/sdc', 'bs=446', 'count=1', 'conv=sync']
0+1 records in
1+0 records out
446 bytes (446 B) copied, 0.00678879 s, 65.7 kB/s
[08:41:50] installing the bootloader to /dev/sdc1.
[08:41:50] ['syslinux', '/dev/sdc1']
[08:41:50] ['parted', '-s', dbus.String(u'/dev/sdc'), 'set', u'1', 'boot', 'on']
[08:41:50] ['mount', '-o', 'loop,ro', '/home/devil/Public/jaunty-desktop-i386.iso', '/tmp/tmpdKVafj']
[08:41:50] ['rm', '-rf', '/media/disk/autorun.inf']
[08:41:50] ['rm', '-rf', '/media/disk/casper']
[08:41:50] ['rm', '-rf', '/media/disk/dists']
[08:41:50] ['rm', '-rf', '/media/disk/install']
[08:41:50] ['rm', '-rf', '/media/disk/isolinux']
[08:41:50] ['rm', '-rf', '/media/disk/md5sum.txt']
[08:41:50] ['rm', '-rf', '/media/disk/pics']
[08:41:50] ['rm', '-rf', '/media/disk/pool']
[08:41:50] ['rm', '-rf', '/media/disk/preseed']
[08:41:50] ['rm', '-rf', '/media/disk/README.diskdefines']
[08:41:50] ['rm', '-rf', '/media/disk/ubuntu']
[08:41:50] ['rm', '-rf', '/media/disk/umenu.exe']
[08:41:50] ['rm', '-rf', '/media/disk/wubi.exe']
[08:41:50] ['rm', '-rf', '/media/disk/.disk']
[08:41:50] ['rm', '/media/disk/casper-rw']
rm: cannot remove `/media/disk/casper-rw': No such file or directory
[08:41:50] ['/usr/share/usb-creator/install.py', '-s', '/tmp/tmpdKVafj/.', '-t', '/media/disk', '-p', '134217728']
Tried to symlink . -> /media/disk/ubuntu
Tried to symlink jaunty -> /media/disk/dists/stable
Tried to symlink jaunty -> /media/disk/dists/unstable
['rm', '-rf', '/media/disk/syslinux']
['mv', '/media/disk/isolinux', '/media/disk/syslinux']
['mv', '/media/disk/syslinux/isolinux.cfg', '/media/disk/syslinux/syslinux.cfg']
['cp', '/media/disk/syslinux/syslinux.cfg', '/media/disk/syslinux.cfg']
Traceback (most recent call last):
  File "/usr/share/usb-creator/install.py", line 156, in <module>
    main(source, target, persist)
  File "/usr/share/usb-creator/install.py", line 134, in main
    popen(['dd', 'if=/dev/zero', 'bs=%sM', 'of=%s/casper-rw' % target, 'count=1' % persist])
TypeError: not all arguments converted during string formatting
[08:44:54] Unmounting source volume.
[08:44:54] ['umount', '/tmp/tmpdKVafj']
[08:44:55] ['rmdir', '/tmp/tmpdKVafj']
[08:44:55] Install command exited with code: 256
[08:44:55] Forcing shutdown of the install process.
[08:44:55] Unmounting source volume.
[08:44:55] ['umount', '/tmp/tmpdKVafj']
umount: /tmp/tmpdKVafj: not found
[08:44:55] ['rmdir', '/tmp/tmpdKVafj']
rmdir: failed to remove `/tmp/tmpdKVafj': No such file or directory
[08:44:55] Install failed.

```

After that, unplug, insert to my laptop
and kubuntu boots...

What strikes me odd, is the second last row.
Failed to remove:  `/tmp/...
there were no folder by that name in temp...

Now I can get rid of my Debian once and for all :D

---

### Post by IanW on 2009-02-23
> **ormandj said:**
> Same problem (I think). I get a window with a red minus icon when it fails, but no error message.

On my system, the window is tall & narrow. It seems as if the error message is off to the right, but I can't resize the box.

As I needed a new install media for my netbook IMMEDIATELY (It hard-locked _during_ an update! ](*,) ), I temporarily downgraded to 0.1.10 from the Intrepid repo.

---

### Post by Starks on 2009-02-23
The usb-creator doesn't fail for me if persistent storage is disabled, but it still throws the whacky prompt.

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/332485](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/332485)

---

