---
title: "EeePC 1005HA Installer won't launch?"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by xirt on 2009-12-30
I'm new to Ubuntu. I got 9.10 UNR and made my USB bootable drive. The first screen pops up with options:
try Ubuntu
Install Ubuntu
mem test
hard disk test
advanced options
etc.
I choose to install.
It starts up and then the logo comes up and disappears and then i would expect an the installer to start but this comes up:

(initramfs) BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) multi-call binary

Usage: mount [flags] DEVICE NODE [-o options,more-options]

Mount a filesystem Filesystem autodetection requires /proc be mounted.

Options:
    -a        Mount all filesystems in fstab
    -f        don't mount
    -i        Don't call /sbin/mount.<filesystem> helper
    -r        REad-only mount
    -t fs-type    Filesystem type
    -w        Read-write mount (default)
-o option:
    loop        Ignored (loop devices are autodetected)
    [a]sync        Writes are asynchronous / synchronous
    [no]atime    Disable / enable updates to inode access times
    [no]diratime    Disable / enable atime updates to directories
    [no]relatime    Disable / enable atime updates relative to modification time
    [no]dev        Allow use of special device files / disallow them
    [no]exec    Allow use of executable files / disallow them
    [no]suid    Allow set-user-id-root programs / disallow them
    [r]shared    Convert [recursively] to a shared subtree
    [r]slave    Convert [recursively] to a slave subtree
    [r]private    Convert [recursively] to a private subtree
    [un]bindable    Make mount point [un]able to be bind mounted
    bind        Bind a directory to an additional location
    move        Relocate an existing mount point
    remount        Remount a moujnted filesystem, changing its flags
    ro/rw        Moount for read-only / read-write

There are EVEN MORE flags that are specific to each filesystem
You'll have to see the written documentation for those filesystems

Can not mount /dev/loop1 on /cow
_

Help please

---

