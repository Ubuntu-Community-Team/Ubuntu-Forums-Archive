---
title: "Partitions turned into ext4?"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by clearscreen on 2009-04-19
Uhm... apparently my ext3 partitions have mysteriously turned into ext4 (I can assure you: I have not converted or formatted them myself), and at boot grub now complains that ext4 format is not supported...

I'm typing this from my 8.10 live cd, and when trying to mount my local partitions I get a similar error:

"The volume uses the ext4 file system which is not supported by your system".


- Why are my drives suddenly tagged as ext4? 
- Reading about ext4 before, grub should be able to boot up by treating them as ext3 drives... I have no idea why grub thinks they're ext4 drives now (some update must have changed my grub config), but what should I install on 8.10 to get ext4 support so I can edit my grub configs?

---

### Post by clearscreen on 2009-04-19
Attempting to mount it on livecd as ext4dev:

[ 1368.104877] EXT4-fs: sda1: not marked OK to use with test code.

---

### Post by clearscreen on 2009-04-19
Fixed above error by using debugfs:

debugfs:  set_super_value s_flags 4 



Still unsure why grub wont boot my ext4 partition (and unsure why it's ext4 in the first place)

---

### Post by clearscreen on 2009-04-19
And back to my normal install... Managed to mount stuff on my livecd, chrooted into my normal ubuntu partition and then executed a grub-install /dev/sda1 --recheck

All fine now :)

---

### Post by alphacrucis2 on 2009-04-19
> **clearscreen said:**
> Fixed above error by using debugfs:

debugfs:  set_super_value s_flags 4 



Still unsure why grub wont boot my ext4 partition (and unsure why it's ext4 in the first place)

The version of grub in the Jaunty Beta does boot from ext4 partition. I originally installed Jaunty on ext3 and then converted the partitions to ext4 using tune2fs & efsck from the live CD. Then edited the fstab. I half expected that grub wouldn't work but it did. Maybe your version of grub didn't get updated?

---

