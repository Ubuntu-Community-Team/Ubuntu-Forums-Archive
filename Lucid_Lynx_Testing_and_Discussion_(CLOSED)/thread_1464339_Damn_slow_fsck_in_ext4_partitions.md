---
title: "Damn slow fsck in ext4 partitions"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Miguel on 2010-04-28
Dear all,

This morning was one of those beautiful mornings in which my beloved T400 would greet me with a wonderful fsck screen during boot. I though I had gotten mostly rid of it, ever since I switched *all* my linux partitions to ext4 (except swap, of course).

The thing is, today the fsck took aaages, between 5 and 10 minutes. OK, this is not life-threatening, but I returned to my kitchen to see take care of the stove. I was surprised, because slow fsck times was one of the big things of ext4. I suspected that some data might have been lost, so I started looking in lost+found folders. There was nothing there, however.

Has anybody experienced very slow fsck times lately? I only found a thread in a casual search more or less related, but these guys were having freezes on boot-up after updating the kernel to -18. The lucid bugs I found in google also didn't seem related.

Regards,

Miguel

PS: This is my fstab, in case anyone wonders:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=deccd0e8-e72a-4b85-bb5c-e2ded564ca8c /               ext4    errors=remount-ro 0       1
UUID=4c1f5e2a-d9b7-41e6-b695-7d13d7efce74 /home           ext4    defaults        0       2
UUID=42779020-0275-44d5-9bfe-0de43244313b /test           ext4    defaults        0       2
UUID=2458F54E58F51F6C /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=a53e32da-7fd2-463c-a4e6-aba3587b7f79 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by philstovell on 2010-04-28
I have exactly the same problem with Lucid RC running in Virtualbox. It's been running a disk check for over 15 minutes and has just reached 78%. Google found me your message. I'll carry on searching (It's now at 79%!).

---

### Post by Miguel on 2010-04-28
Thanks for your reply, philstovell

I'd like to add some more data. Since fsck times are clearly related to disk size and perhaps free space, this is the size of my partitions:

```

$ LANG=en_US df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              33G  5.4G   26G  18% /
none                  1.9G  388K  1.9G   1% /dev
none                  1.9G  864K  1.9G   1% /dev/shm
none                  1.9G   92K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
none                   33G  5.4G   26G  18% /var/lib/ureadahead/debugfs
/dev/sda7              11G  156M   11G   2% /test
/dev/sda2              96G   71G   25G  75% /windows
/dev/sda6              88G   12G   72G  14% /home

```

Could I have had a race condition between ureadahead and fsck? This is, BTW, 64 bit ubuntu, and the HD is a 5400 rpm (Seagate Momentus 5400.4).

---

### Post by The Recorder on 2010-04-28
Same problem here.  Can it have something to do with yesterday's full update of Plymouth?

---

### Post by mc4man on 2010-04-28
See the same thing, though because the slowdown starts at 70% would consider it suspect.

By comparison after removing "quiet splash" from grub the fsck runs in less than 30 secs. (60 GB, 6.3 used

boot log shows the same whether < 30 secs or 5 min's,

---

### Post by BrokeMahPC on 2010-04-28
It was doing that to me and I have had issues with it on lucid since fsck first ran, it would get to 72% and then the GDM would start. Was unable to tell if that was a Plymouth problem.
I recently installed the 2.6.34-020634rc5-generic kernel to try to solve my ATI KMS problems and it runs correctly there but only detects 1 of the hard drives (both sata, not in raid config).

---

### Post by NZjelle on 2010-04-28
I had similar problem this morning. fsck dedided it wanted to check all 4 of my disk partitions. This is the first time ever that it wanted to check all 4 at the same time. Started on 1 of 4. Progressed quickly to about 74%. Then moved agonisingly slowly and seemingly haltingly up to 90%. Then it decided it had enough and booted me straight to the desktop without further checking.

---

