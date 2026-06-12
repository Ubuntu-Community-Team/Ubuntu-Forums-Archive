---
title: "Connecting existing Linux RAID to new system."
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by daz555 on 2013-11-11
Hi, all. Nice to be here.

Below is my current disk config - 10.04 server installed on USB flash drive with 2 3TB hard drives containing all my data:

fstab:
UUID=975aecd2-e9d6-4916-887f-a4b3f370fab0 / ext4 noatime,errors=remount-ro 0 1
/dev/sda2 /mnt/sata1 ext4 defaults 0 0
/dev/sdb2 /mnt/sata2 ext4 defaults 0 0
/dev/md0 /mnt/raid1 ext4 defaults 0 0

(I have stripped out the non relevant entries in fstab related to RAMdisks etc)

mdadm:
DEVICE /dev/sda1 /dev/sdb1
ARRAY /dev/md0 level=raid1 devices=/dev/sda1,/dev/sdb1

The drives are currently connected to a 10.04 Server installation and all is well. However, I am installing 12.04 on a new boot disk as part of a my move from 32bit to 64bit.

I'm busily chugging away at the new build, updating it and installing/configuring the software I'll need for when I eventually switch over.

The hard drives containing my data have not yet been connected to the new build and I want to make sure I get this part right. What will happen to volumes when I connected them up and boot into 12.04? Will it detect the RAID volumes automatically or is there something I need to do either before or after first boot to ensure that the RAID volume is correctly mounted and more importantly that no RAID config is wiped out.

Thanks in advance.

---

### Post by daz555 on 2013-11-11
90 views and no replies. Now wondering if I'm missing something obvious and my question is simply not suitable.

Do I need to add anything else in terms of detail?

---

### Post by daz555 on 2013-11-11
Right, I decided to backup the 250GB of data on my RAID 1 volume and just get stuck in and see what happened.

I connected the disk and booted up - nothing (as I expected).

I then added the relevant entries from my OP back into fstab and mdadm and rebooted. BINGO. Solved.

Excellent.

---

