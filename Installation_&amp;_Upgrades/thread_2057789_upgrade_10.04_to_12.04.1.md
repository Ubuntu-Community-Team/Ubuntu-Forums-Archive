---
title: "upgrade 10.04 to 12.04.1"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by holli73 on 2012-09-14
hello,

i did an upgrade from my 10.04 to 12.04 on my headless ubuntu server - everything worked fine but it did not restart anymore...

i was able to figure out why through my serial console - the problem seems that the md raid for boot is always changing on reboot...

f.ex.

i had /dev/md0 where my /boot is located

```
md0: active raid1 sdc1[2] sdd1[3] sda1[0] sdb1[1]
      192640 blocks [4/4] [UUUU]
```

after the update i wouldn't boot because the name changed to

```
md126 : active raid1 sdc1[2] sdd1[3] sda1[0] sdb1[1]
      192640 blocks [4/4] [UUUU]
```

so i changed the fstab to that device but everytime i do a reboot this is changing back and forth - i tried:

```
sudo mdadm --assemble --update=super-minor /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

but didn't help as well...

i have 4 internal drives + 2 usb drives and another 8 esata devices all defined as raids - but on every reboot this system will not boot because the /dev/md* is changing and i have to edit the fstab to fit the new names to proceed on booting...

```
md4 : active raid0 sdf1[1] sde1[0]
      488391808 blocks 4k chunks
      
md126 : active raid1 sdc1[2] sdd1[3] sda1[0] sdb1[1]
      192640 blocks [4/4] [UUUU]
      
md127 : active raid10 sdj1[3] sdk1[4] sdn1[7] sdi1[2] sdg1[0] sdl1[5] sdh1[1] sdm1[6]
      7814047744 blocks 256K chunks 2 far-copies [8/8] [UUUUUUUU]
      
md2 : active raid5 sdc6[2] sdb6[1] sdd6[3] sda6[0]
      4101562368 blocks level 5, 256k chunk, algorithm 2 [4/4] [UUUU]
      
md1 : active raid10 sdc5[2] sdb5[1] sda5[0] sdd5[3]
      19534848 blocks 256K chunks 4 far-copies [4/4] [UUUU]
      
md3 : active raid0 sdc7[2] sdb7[1] sda7[0] sdd7[3]
      312881152 blocks 256k chunks
```

any idea why the /boot = /dev/md126 will not stay as md0 after reboot or will become 127,.. ?
it can not be the devices itself because doesn't matter what mdx i get - it is always sd[abcd]1 

any help would be great

thanks
holli

PS: ```
Linux holli-nas-2 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by SlugSlug on 2012-09-14
not sure why but try using the UUID in fstab instead of /dev/md0

```
sudo blkid
```
 will show UUID

---

### Post by holli73 on 2012-09-14
hello,

with the UUID at least it boots but the /dev/md0 is always jumping between 0 und 126 - at least it is not a problem anymore during boot...

what i don't understand why /etc/mdadm/mdadm.conf is not considered/taken

```
holli@holli-nas-2:~$ cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=4 devices=/dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
ARRAY /dev/md1 level=raid10 num-devices=4 UUID=def13301:78eeb488:af65d04a:344214eb
ARRAY /dev/md2 level=raid5 num-devices=4 UUID=1a6cdedb:c914dfc2:dcf2f1c9:1ae668f3
ARRAY /dev/md3 level=raid0 devices=/dev/sda7 /dev/sdb7 /dev/sdc7 /dev/sdd7
ARRAY /dev/md4 level=raid0 devices=/dev/sde1 /dev/sdf1
ARRAY /dev/md5 level=raid10 devices=/dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1 /dev/sdk1 /dev/sdl1 /dev/sdm1 /dev/sdn1
```

f.ex. md5 is now 127

thanks
holli

---

### Post by SlugSlug on 2012-09-14
read one post saying to remove dmraid package - but I dnt know

---

