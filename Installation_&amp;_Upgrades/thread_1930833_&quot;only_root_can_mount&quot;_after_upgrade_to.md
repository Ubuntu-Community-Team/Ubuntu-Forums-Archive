---
title: "&quot;only root can mount&quot; after upgrade to"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by Kilarin on 2012-02-24
I was using ubuntu 11.04 and refused to upgrade to 11.10 because I dont want a phone gui on my desktop.  I installed the xubuntu gui, and, since its been working ok for months now, I decided it was time to go ahead and upgrade ubuntu to 11.10 using the standard upgrade button.

Everything went smooth as glass, after the upgrade I've still got my xfce gui.  BUT, suddenly a 500 gig hard drive wont mount.  Every time I boot I have to hit "I" on the xfce boot splash to ignore the mount error.  When I try to mount the hard drive through the gui I get the following:

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdd1 on /media/disk

when I try to mount from the command line I get:
$ mount /dev/sdd1 /media/disk
mount: only root can do that

I have to use sudo to mount it.  Which works, but thats just silly.  This was working fine before the upgrade.

Further info:  (these are with the drive mounted using sudo)
-----
sudo fdisk -l  for this drive shows:

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7839511

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   976768064   488384001    7  HPFS/NTFS/exFAT
-----

mount for this drive shows:

/dev/sdd1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
-----

$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2012-02-24 06:41 1AB82740B8271A31 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2012-02-24 06:41 2c9724f4-ce1a-4c8f-99df-bc4e0afd2e06 -> ../../sda2
lrwxrwxrwx 1 root root 10 2012-02-24 06:45 3E10D3D910D395ED -> ../../dm-0
lrwxrwxrwx 1 root root 10 2012-02-24 06:41 80D4-988A -> ../../sdb1
lrwxrwxrwx 1 root root 10 2012-02-24 06:41 96C810A5C8108621 -> ../../sda1
lrwxrwxrwx 1 root root 10 2012-02-24 06:41 C6A430F8A430ED15 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2012-02-24 06:41 c7db128c-6813-4f54-8b52-08e585f06e12 -> ../../sda3

-----
/etc/fstab for this drive shows:
# Entry for internaly remounted 500gp usb drive /media/disk
UUID=C6A430F8A430ED15                      /media/disk    ntfs-3g      defaults,umask=007,uid=1000,gid=1000,locale=en_US.UTF-8,nobootwait  0  2

-----
and fstab hadn't been modified this year.

I tried changing the fstab to :
UUID=C6A430F8A430ED15                      /media/disk    ntfs-3g      defaults,umask=007,user,uid=1000,gid=1000,locale=en_US. UTF-8,nobootwait 0 2

but that didn't make any difference.

-----

for permissions I have:
/$ ls -l
drwxr-xr-x  19 root root  4096 2012-02-24 06:48 media
/media$ ls -l
drwxrwxrwx 1 root   root   8192 2011-10-30 20:41 disk

What changed with the upgrade, and how do I fix this so it will mount normally?  I searched for "only root can mount" and found a lot of places where people had discussed the issue, but none that had a solution listed that applied or worked.

Thanks in advance for you help!

---

### Post by agillator on 2012-02-24
If you check, I suspect that your fstab was in fact changed when you upgraded. Your old fstab probably had the option allowing users to mount and that got dropped during the upgrade. Check the options for fstab (and mount) and then add the desired options to the line that is giving you problems.

---

### Post by Kilarin on 2012-02-24
[quote="agillator"]Check the options for fstab (and mount) and then add the desired options to the line that is giving you problems.[/quote]
From what I found researching this issue, thats the "user" option.

I tried:
UUID=C6A430F8A430ED15 /media/disk ntfs-3g defaults,umask=007,user,uid=1000,gid=1000,locale=en_US. UTF-8,nobootwait 0 2

and still got the same error.

---

### Post by roelforg on 2012-02-24
use sudo to exec the mount command.
It's default security.

EDIT: Didn't read the entire post...

---

### Post by agillator on 2012-02-24
Before going any further, in your post you appear to have 'locale=e<space>n_US' in the options. Is that space really there or was that just a product of the copy/paste/post process? If it is really there, that could be your problem. The entire set of options could be ignored because of an error like that. If not, we'll dig a little deeper but let's eliminate the easy and sneaky first.

I also noticed the US.<space>UTF after I reread. The .<space> may be errors, also. The . should be a , and that space may be ok but try taking it out (if it is there) anyway.

---

### Post by Kilarin on 2012-02-24
[quote=""]in your post you appear to have 'locale=e<space>n_US' in the options.[/quote]
ARGH!  I hate it when its something stupid.  re-did it and now it works.
thanks!

---

### Post by Kilarin on 2012-02-24
ok, I spoke to soon.  the drive now mounts.  BUT, I still have to hit "I" (twice) to ignore errors during boot.  boot.log shows the following:

----------------

[   49.663015] apm: BIOS not found.
[   49.697398] init: failsafe main process (997) killed by TERM signal
[   49.700970] init: apport pre-start process (1143) terminated with status 1
[   49.758908] init: apport post-stop process (1211) terminated with status 1
[   49.767284] init: gdm main process (1210) killed by TERM signal
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
udevd[398]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/95-calibre.rules:2


udevd[398]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/95-calibre.rules:2


fsck from util-linux 2.19.1
fsck: fsck.ntfs-3g: not found
fsck: Error 2 while executing fsck.ntfs-3g for /dev/sdb1
mountall: fsck /media/disk [916] terminated with status 8
mountall: Unrecoverable fsck error: /media/disk
fsck: fsck.ntfs-3g: not found
fsck: Error 2 while executing fsck.ntfs-3g for /dev/sda1
mountall: fsck /media/sda1 [395] terminated with status 8
mountall: Unrecoverable fsck error: /media/sda1
/dev/sda2: clean, 506050/14827520 files, 10298735/29643941 blocks
Ignoring errors with /media/disk at user request
Ignoring errors with /media/sda1 at user request

---

### Post by Kilarin on 2012-02-24
all fixed.

The calibre error was an easy patch, just changed BUS to SUBSYSTEM as it requested.

The disk problem solution is here:
[http://ubuntuforums.org/archive/index.php/t-1860114.html](http://ubuntuforums.org/archive/index.php/t-1860114.html)

Can't do chkdsk on a ntfs partition.  so I just changed my fstab from:
UUID=C6A430F8A430ED15                      /media/disk    ntfs-3g      defaults,umask=007,user,uid=1000,gid=1000,locale=en_US.UTF-8,nobootwait  0  2

to:
UUID=C6A430F8A430ED15                      /media/disk    ntfs-3g      defaults,umask=007,user,uid=1000,gid=1000,locale=en_US.UTF-8,nobootwait  0  0

(had to fix both drives of course)

thank you.

---

### Post by agillator on 2012-02-24
Kilarin, just remember that, when dealing with computers as well as most other things in life, there are two kinds of people: those who have and those who will! 

Glad everything is working. Glad I was able to help. I was hoping we weren't going to have to apply the final rule of fixing computers: if at first you don't succeed, get a bigger hammer.

---

### Post by Kilarin on 2012-02-24
[quote=""]I was hoping we weren't going to have to apply the final rule of fixing computers: if at first you don't succeed, get a bigger hammer.[/quote]
Ha!  Beware of programmers carrying screwdrivers. :)

---

