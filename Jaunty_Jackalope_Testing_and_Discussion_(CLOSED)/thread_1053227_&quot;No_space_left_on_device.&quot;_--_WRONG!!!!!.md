---
title: "&quot;No space left on device.&quot; -- WRONG!!!!!!!!!!!"
date: 2009-01-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-01-28
Why does Jaunty insist on throwing me these kinds of errors when I still have 70 GB of free space on both my root and home partitions?

---

### Post by birddog165 on 2009-01-28
I'm sorry, i'm an idiot today

---

### Post by Starks on 2009-01-28
Never mind. apt-get clean fixed it.


EDIT: It's back.

---

### Post by chrisccoulson on 2009-01-28
Not using ext4 by any chance are you?

[http://lkml.org/lkml/2009/1/21/177]("http://lkml.org/lkml/2009/1/21/177")

---

### Post by Starks on 2009-01-28
I've been switching back and forth between ext3 and ext4 for my installs. I'm currently using ext3.

---

### Post by Cope57 on 2009-01-28
Your root partition was full while your home partition was fine.
Maybe resizing your / root partition, so you are less likely to have this issue. Use the liveCD to do so.

---

### Post by Starks on 2009-01-28
Heh. I was running ext4 after all... Anyway fsck fixed the problem.

```
eric@kingfisher:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              70G  3.1G   64G   5% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  212K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M   68K 1003M   1% /dev
tmpfs                1003M   88K 1003M   1% /dev/shm
lrm                  1003M  2.0M 1001M   1% /lib/modules/2.6.28-5-generic/volatile
/dev/sda3              70G  4.3G   63G   7% /home
/dev/sdb1             3.9G  704M  3.2G  18% /media/RESCUE
```

---

### Post by Starks on 2009-02-24
This is happening more and more.

At least once a day I'm getting this.

---

### Post by Archmage on 2009-02-24
Are you using ext3 and ext4 for the same partition? That it is no wonder that you are getting problems. Once you use a partition as ext4 you shouldn't go back, since it use extenstions that ext3 can't handle.

---

### Post by perlluver on 2009-02-24
I was having the same problem on a straight ext4 partition, with no separate root.  I had to re-install to fix it.

---

### Post by Starks on 2009-02-24
> **Archmage said:**
> Are you using ext3 and ext4 for the same partition? That it is no wonder that you are getting problems. Once you use a partition as ext4 you shouldn't go back, since it use extenstions that ext3 can't handle.

You are mistaken about my setup.

/root and /home are both ext4 partitions.

---

### Post by Kow on 2009-02-25
> 
  * ext4: Add support for non-native signed/unsigned htree hash algorithms
  * ext4: tone down ext4_da_writepages warnings
  * ext4: Fix the delalloc writepages to allocate blocks at the right
    offset.
  * ext4: avoid ext4_error when mounting a fs with a single bg
  * ext4: Widen type of ext4_sb_info.s_mb_maxs[]
  * jbd2: Add barrier not supported test to journal_wait_on_commit_record
  * ext4: Don't overwrite allocation_context ac_status
  * ext4: Add blocks added during resize to bitmap
  * ext4: Use EXT4_GROUP_INFO_NEED_INIT_BIT during resize
  * ext4: cleanup mballoc header files
  * ext4: don't use blocks freed but not yet committed in buddy cache init
  * ext4: Fix race between read_block_bitmap() and mark_diskspace_used()
  * ext4: Fix the race between read_inode_bitmap() and ext4_new_inode()
  * ext4: Use new buffer_head flag to check uninit group bitmaps
    initialization
  * ext4: mark the blocks/inode bitmap beyond end of group as used
  * ext4: Don't allow new groups to be added during block allocation
  * ext4: Init the complete page while building buddy cache
  * ext4: Fix s_dirty_blocks_counter if block allocation failed with
    nodelalloc
  * ext4: Add sanity checks for the superblock before mounting the
    filesystem
  * ext4: only use i_size_high for regular files
  * ext4: Add sanity check to make_indexed_dir
  * ext4: Initialize the new group descriptor when resizing the filesystem
  * Fix longstanding "error: storage size of '__mod_dmi_device_table' isn't
    known"
  * Linux 2.6.28.7


linux-image-2.6.28-8.25 changelog... Perhaps this widely known bug is finally resolved?

---

### Post by jlacroix on 2009-02-25
This happened to me once, but after that it's never happened to me again. It happened when I was updating.

---

### Post by Starks on 2009-02-25
> **jlacroix said:**
> This happened to me once, but after that it's never happened to me again. It happened when I was updating.

That's when I usually notice it.

---

### Post by fictivetoast on 2009-02-26
Experiencing the same problem here on ext4, and it's preventing the new round of updates from installing without all sorts of aweful errors... I've got 7 gigs free on root.  Anyone have any leads?

---

### Post by Yes_It's_Me on 2009-02-26
This has happened a few times for me on my jaunty ext4 machine. There is certainly a problem with ext4, though it's not too serious.

The issue is usually resolved when doing a fsck upon boot. To do this:

```
sudo touch /forcefsck
```

in a terminal. This will create a forcefsck file in the root of your filesystem, this will trigger fsck to check your filesystem on the next boot before the disk is mounted.

After that, it stops complaining and the file is removed automatically.

---

### Post by caryb on 2009-03-01
I had the same problem today, I couldn't touch the file as I didn't have the disk space (142G free) I rebooted in recovery mode & created the forcefsck file then rebooted. I too was doing upgrades when I ran out of space:confused:


Cary

---

### Post by Gina on 2009-03-01
I've had it happen in the past too.  Though not recently.  (Famous last words!)

---

