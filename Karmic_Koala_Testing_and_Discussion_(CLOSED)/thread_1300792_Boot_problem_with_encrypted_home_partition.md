---
title: "Boot problem with encrypted home partition"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by McLem0n on 2009-10-25
Hi guys,

I just checked out the RC of Ubuntu 9.10 and activated the home encryption in the installer. The problem is that every time I boot Ubuntu the following messages appear multiple times: 
```
One or more of the mounts listed in /etc/fstab cannot yet be mounted
swap:waiting for /dev/mapper/cryptswap1
Press ESC to enter a recovery shell
```
After this message the system boots up without any problem.
My **/var/log/boot** contains nothing although I changed **BOOTLOGD_ENABLE=No** to **BOOTLOGD_ENABLE=Yes** in **/etc/default/bootlogd**.
Here is my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=184e114f-fe3a-4a3a-a4ce-dca15e935e47 /               ext4    errors=remount-ro 0       1
#/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

I'm running Ubuntu 9.10 on a MacBook Pro 4,1 but I don't think it's a specific Mac problem because under 9.04 the /home encryption worked without any problems.
Has anyone an idea what the problem is?

And yes I know Ubuntu 9.10 isn't stable yet. ;)

Greetings, 
McLem0n

---

### Post by bcasanov on 2009-10-25
I'm having this same problem too.  I chose to have an encrypted home directory when I did a fresh install of Karmic, and I keep getting very similar types of messages when booting up.

---

### Post by fdmille on 2009-10-25
I'm getting the same errors too.  Help is appreciated.

---

### Post by picopir8 on 2009-10-25
I had the same problem as well but reinstalled and did not choose an encrypted homefs on the second go-around.

Anyway, I believe that a particular service is required before encrypted homefs images can be mounted and that service is not yet available.  So it complains and retrys until it finally succeeds.

This could be as simple as changing the order of some of the init scripts.

Otherwise, homefs could be removed from fstab and then mounted by an init script that runs after everything else has had a chance to run.

---

### Post by cudjoe on 2009-10-27
Same here.

I sometimes have to enter twice my passphrase. But then it boots normally.

Did someone fill a bug report on upstart or cryptsetup ?

---

### Post by bcasanov on 2009-10-27
The same problem is happening to a lot of people.  Look at  related thread: [http://ubuntuforums.org/showthread.php?t=1301766&highlight=mounts+%2Fetc%2Ffstab](http://ubuntuforums.org/showthread.php?t=1301766&highlight=mounts+%2Fetc%2Ffstab)

---

### Post by bcasanov on 2009-10-29
Has there been a bug filed about this?

---

### Post by humphreybc on 2009-10-29
Don't do anything, don't press any keys, just let it continue to boot.

It doesn't get mounted until you logon, so therefore it's just giving you a warning saying it can't be mounted yet.

---

### Post by kansasnoob on 2009-10-29
> **bcasanov said:**
> Has there been a bug filed about this?

[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/428435](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/428435)

---

