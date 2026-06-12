---
title: "New generic kernel cannot boot to single user mode?"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by carfield on 2009-10-20
Due to [http://ubuntuforums.org/showthread.php?t=1278374](http://ubuntuforums.org/showthread.php?t=1278374) , but after boot upgrade kernel version to linuz-2.6.31-14-generic, I am not able to boot to shell for single user mode .

In initramfs , /dev/sda and /dev/sdb are not able to found also

---

### Post by VMC on 2009-10-20
> **carfield said:**
> Due to [http://ubuntuforums.org/showthread.php?t=1278374](http://ubuntuforums.org/showthread.php?t=1278374) , but after boot upgrade kernel version to linuz-2.6.31-14-generic, I am not able to boot to shell for single user mode .

In initramfs , /dev/sda and /dev/sdb are not able to found also

You could have just made a new post instead of opening another thread.

I'm confused with your second sentence. Expand on it a little.

I'm guessing that you can still get grub2 menu.

Now "ranch hand" asked for you to get a livecd. Did you get one? You need to be able to run linux somehow.

I would like to see your hard disk structure to start with:

```
sudo fdisk -l
```

and

```
sudo blkid
```

---

### Post by carfield on 2009-10-21
HI, if I boot with linux-2.6.31-14-generic, nothing is print.

But if I boot with previous version of kernel, linux-2.6.28-14-generic, here is the result I can see

root@carfield:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d931f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59572   478512058+  83  Linux
/dev/sda2           59573       60801     9871942+   5  Extended
/dev/sda5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ddb1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59572   478512058+  83  Linux
/dev/sdb2           59573       60801     9871942+   5  Extended
/dev/sdb5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/sdc: 4026 MB, 4026531840 bytes
220 heads, 32 sectors/track, 1117 cylinders
Units = cylinders of 7040 * 512 = 3604480 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1118     3932144    c  W95 FAT32 (LBA)
root@carfield:~# blkid
/dev/sda1: UUID="7b566603-851c-43f0-8ec5-2098655bb611" TYPE="ext4" 
/dev/sda5: UUID="3d022ce4-c764-4fd1-9c2a-c776c1da1454" TYPE="swap" 
/dev/sdb1: UUID="80886562-7160-4bc5-9730-c32f0a24ac68" TYPE="ext4" 
/dev/sdb5: UUID="121f3557-c69e-fbaa-695d-e34f864aaece" TYPE="linux_raid_member" 
/dev/sdc1: LABEL="" UUID="72F6-F7F3" TYPE="vfat"

---

### Post by csbac on 2009-10-23
Hi!
I cannot boot into single user mode, either.
It is a vmware install, so, no previous installations.
I have the trouble on two systems, one started with alpha5 and just upgraded, the other one istalled initially a bit later and upgraded several times, last time yesterday.

For using "zerofree", I need to remount / ro.
* select (recover) from grub2 menu
* get the dialog to select various kinds of recovery
* select root shell (last)
* drop into root shell, though I usally don't even get that far
* get background(!) message that a mount error occurred. Everything is mounted correctly, though, and normally, the boot continues.
* have a shell prompt that does not really work ...
** no newline
** after "reset", newlines work, but regularly, additional characters are inserted into commands I type. Possibly, the dialog or some other console app is still running in the background
* even with killing/stopping rsyslog, console-kit-daemon, dbus, vmware-tools (all that fuser -vm / showed as F), / is still too busy to remount -ro
* after exiting this shell, I get the usual 6 login screens
* logging in there, and killing/stopping the services above, / is still busy.

I now managed to achieve what I wanted by "init=/bin/bash".
That's no solution, though ... what can the mount error be?
Also, I'm not sure wether zerofree is actually writing anything in this mode ...

I am a bit suprised about the entries in /etc/fstab for
/media/cdrom1 /dev/scd0 user,noauto,...
/media/cdrom0 /dev/scd1 user,noauto,...
/media/floppy0 /dev/fd0 user,noauto,...
on both systems, having only on CD (/dev/scd0->sr0) and no floppy (but a floppy device) .. maybe this is the reason for the "mount" error on single user boot?

Yours,
Sebastian

Additions:
* after correcting fstab, the recovery dialog runs better ... no "mount error".
* yet, "key down" and "up" in the recovery dialog works only very unregularyly ... tab, on the other handy, and return, work w/o problems.
* after "resuming boot", logging in (console only), and "telinit 1", the recovery dialog has usable arrow keys.
* after stopping rsyslog, remount ro is possible.

Next time, mount error is back - either the arrows to not react, or I get a mount error ... 
"""
mountall: Cancelled
General Error mounting filesystems.
A maintenance shell will now be started.
Control-D will terminate this shell and re-try
ubuntu:~#
"""
Ctrl+D does not do anything, "exit" results in some further steps ...
* a message that swap cannot be mounted b/c it is already mounted
* some more services startup 
and ... no further reaction.

Sebastian

---

### Post by carfield on 2009-10-23
I see... great work , thx. 

For me I just boot to Virtual Kernel, then install previous Kernel (2.8.2x) to boot

> **csbac said:**
> Hi!
I cannot boot into single user mode, either.
It is a vmware install, so, no previous installations.
I have the trouble on two systems, one started with alpha5 and just upgraded, the other one istalled initially a bit later and upgraded several times, last time yesterday.

For using "zerofree", I need to remount / ro.
* select (recover) from grub2 menu
* get the dialog to select various kinds of recovery
* select root shell (last)
* drop into root shell, though I usally don't even get that far
* get background(!) message that a mount error occurred. Everything is mounted correctly, though, and normally, the boot continues.
* have a shell prompt that does not really work ...
** no newline
** after "reset", newlines work, but regularly, additional characters are inserted into commands I type. Possibly, the dialog or some other console app is still running in the background
* even with killing/stopping rsyslog, console-kit-daemon, dbus, vmware-tools (all that fuser -vm / showed as F), / is still too busy to remount -ro
* after exiting this shell, I get the usual 6 login screens
* logging in there, and killing/stopping the services above, / is still busy.

I now managed to achieve what I wanted by "init=/bin/bash".
That's no solution, though ... what can the mount error be?
Also, I'm not sure wether zerofree is actually writing anything in this mode ...

I am a bit suprised about the entries in /etc/fstab for
/media/cdrom1 /dev/scd0 user,noauto,...
/media/cdrom0 /dev/scd1 user,noauto,...
/media/floppy0 /dev/fd0 user,noauto,...
on both systems, having only on CD (/dev/scd0->sr0) and no floppy (but a floppy device) .. maybe this is the reason for the "mount" error on single user boot?

Yours,
Sebastian

Additions:
* after correcting fstab, the recovery dialog runs better ... no "mount error".
* yet, "key down" and "up" in the recovery dialog works only very unregularyly ... tab, on the other handy, and return, work w/o problems.
* after "resuming boot", logging in (console only), and "telinit 1", the recovery dialog has usable arrow keys.
* after stopping rsyslog, remount ro is possible.

Next time, mount error is back - either the arrows to not react, or I get a mount error ... 
"""
mountall: Cancelled
General Error mounting filesystems.
A maintenance shell will now be started.
Control-D will terminate this shell and re-try
ubuntu:~#
"""
Ctrl+D does not do anything, "exit" results in some further steps ...
* a message that swap cannot be mounted b/c it is already mounted
* some more services startup 
and ... no further reaction.

Sebastian

---

### Post by csbac on 2009-10-24
I just remembered I installed both version with vmware "easy install".
Apparently, vmware added a second cd drive when installing the additions, b/c the ubuntu image was still locked. Therefor, two cd drives, of which only one is "physically" available after installation.

I tried again using the -rc and a normal install.
Same problems with single user mode.
Only one CD drive, no floppy (none configured for machine).
Still "mount error" in single user mode, dropping to no-newline-shell at the same time as runing the recovery selection dialog ...
2.6.31-14-generic #48 SMP

Same situation after upgrade (24.10.09, 10:00 AM CEST(UTC+2))

Although, if I'm very(!) careful with key presses, I manage to get to the "root shell prompt" ... very strange. Ctrl+D, back to dialog. Again, root shell, Ctrl+D, back to dialog. Moving around with arrow keys, mount error.
Are the key presses triggering something they shouldn't????????

Sebastian

BTW ... / is mounted rw, which in some way defies the sense of single user mode ...
stop rsyslog, stop dbus, stop avahi-daemon, killall console-kit-daemon
/ still too busy for ro.

---

