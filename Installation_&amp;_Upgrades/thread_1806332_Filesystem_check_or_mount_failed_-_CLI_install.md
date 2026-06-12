---
title: "Filesystem check or mount failed - CLI install"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by ThePilch on 2011-07-17
Hi,

I've recently come to linux, and just installed the CLI. When i boot, i eventually get:

Filesystem check or mount failed
A maintenance shell will now be started...etc.

What i've tried so far:

efsck sda1 : no errors
mount -a : mount: special device /dev/sdb1 does not exist
fdisk -l : disk /dev/dm-0 doesnt contain a valid partition table (nor does /dev/dm-1)

Fstab:

proc /proc proc nodev,noexec,nosuid 0 0
/dev/mapper/serveric-root/ ext4 errors=remount-ro 0 1
/dev/sdb1 /boot ext2 defaults 0 2
/dev/mapper/serveric-swap_1 none swap sw 0 0

Any help would be appreciated.

Richard

---

### Post by psusi on 2011-07-17
Do you have a second disk?  It appears to have gone missing.

---

### Post by ThePilch on 2011-07-17
i have one disk, which i think was split into 2 partitions upon install
and a dvdrom

thats all...

Since its a fresh install, i dont mind trying anything :D mind you its not the first time ive tried reinstalling either...

Richard

---

### Post by psusi on 2011-07-17
Then why did you edit your fstab and set it to mount /boot on /dev/sdb1?

---

### Post by ThePilch on 2011-07-17
i didnt,

i opened my Fstab to post the contents on here.

My experience with linux = 0, i thought it might help you guys help me.

Richard

---

### Post by psusi on 2011-07-18
Well someone added that entry.  If it wasn't you, then who?  Did you create a /boot partition in the installer?

---

