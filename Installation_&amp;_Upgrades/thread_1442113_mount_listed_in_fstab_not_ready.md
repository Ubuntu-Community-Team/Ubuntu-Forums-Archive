---
title: "mount listed in fstab not ready"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by rockhoppe7 on 2010-03-29
Hi, I recently put my /home folder on a separate partition (sda3), by following these instructions: [www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome").  

All went well (after I chmod-ed the permissions for .ICEauthority), except that now during the boot sequence I get this message:

"One or more of the mounts listed in fstab cannot yet be mounted.
Waiting for sda3
press Esc to enter a recovery shell"

Two or three seconds later, the boot continues, and sda3 mounts - when the system comes up, /home is fully read/writeable.

Can anyone tell me why fstab can't see my new partition from the start?

Thanks

FYI, my fstab looks like this (I don't know why there are commented-out lines - I guess it was when I upgraded from 9.04 to 9.10 - I did an 'upgrade', not 'fresh install').
I'm not sure what difference the 'nodev' and 'nosuid' parameters are in the last new line - I was just following the instructions, but quick searching suggest this is not the problem.

I'd be grateful for any help.

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7965dc5c-001c-4221-a273-45a9e12e1179 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=908f4a24-f843-4209-b39b-734ba36cfe48 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2

```

---

### Post by nitstorm on 2010-03-29
Not all that sure about ur prob but i had a similar problem, said swap was missing, some UUID error

so i put in *blkid  *in the terminal got the UUID for the swap partition and put it back in fstab, if u have a similar thing or jus want to check out what my prob was, here is the link
[http://ubuntuforums.org/showthread.php?t=1428166](http://ubuntuforums.org/showthread.php?t=1428166)

---

### Post by rockhoppe7 on 2010-03-30
Thanks for the reply, nitstorm.

I don't think the problem is the same - your swap partition was not recognized by your machine even after you created it because it wasn't in your fstab file - once you listed it in fstab, it ran fine.

My partition IS listed in fstab, but the system doesn't see it on boot. I get:

"One or more of the mounts listed in fstab cannot yet be mounted. Waiting for sda3"

..for a few seconds before it comes up as normal.

Anyone got any suggestions?  Is it something to do with Grub - or some other part of the boot process?

---

### Post by rockhoppe7 on 2010-04-01
anyone? :-)

---

### Post by garvinrick4 on 2010-04-01
Did you add it to fstab yourself? Do you want it to mount or just show up in Under Places drop down unmounted but 
ready to mount if need be.

---

### Post by rockhoppe7 on 2010-04-02
I did add it manually, as per the instructions I followed: 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I want it to mount normally - because my /home is on it.

The weird thing is that it DOES mount, but only after the boot message:
"One or more of the mounts listed in fstab cannot yet be mounted. Waiting for sda3"

I don't understand why this is happening.  I suppose my worry is that it has some problem if it's not mounting properly.

Thanks

---

### Post by garvinrick4 on 2010-04-02
You know if I were you I would start a new thread and ask  if someone would
post there fstab with a /home installed on a partition.
 You can then see what it looks like and if yours is right. I do not have a seperate /home so have nothing to compare yours with.

If it is not mounted on desktop do these lines of code mount it?

sudo mkdir /media/home  (make a directory)
sudo mount /dev/sda3 /media/home  (mount the partition)

sudo umount /media/home (to unmount not a typo umount is right)

---

