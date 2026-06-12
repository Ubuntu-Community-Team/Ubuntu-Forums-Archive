---
title: "understanding fdisk -l"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by AnLGP on 2012-09-30
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   307564424   153782181   83  Linux
/dev/sda2       307564425   466350884    79393230   83  Linux
/dev/sda3       466352126   625141759    79394817    5  Extended
/dev/sda5       466352128   616900607    75274240   83  Linux
/dev/sda6       616902656   625141759     4119552   82  Linux swap / Solaris

Is the device with the * the current mounted partition?

I have the other two Linux partitions which I am attempting to delete and merge, but I want to make sure I keep the current partition I am on in tact.

One is a micro distro I am deleting the other is just a formatted partition with nothing on it.

Thanks!

---

### Post by darkod on 2012-09-30
No, the * means the boot flag and only one partition on the hdd can have it.
When linux is booted you can easily see what is mounted and where with:
df -h

Also, many times parted gives you better presentation of your disk partition and you can change the units ti MiB, GiB, sectors, etc.
sudo parted unit MiB -l
sudo parted -l (shows sectors by default)

---

### Post by AnLGP on 2012-09-30
/dev/sda5        71G   27G   41G  40% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           777M  908K  776M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G   80K  1.9G   1% /run/shm


This is df -h, so this would be the current partition (/dev/sda5)?

---

### Post by darkod on 2012-09-30
Yes, sda5 mounted as /.

I forgot to mention, df -h doesn't show the swap partition but you can already see in the fdisk results that swap is sda6.

---

### Post by AnLGP on 2012-09-30
> **darkod said:**
> Yes, sda5 mounted as /.

I forgot to mention, df -h doesn't show the swap partition but you can already see in the fdisk results that swap is sda6.

Thank you!  I'll marked as solved.

---

