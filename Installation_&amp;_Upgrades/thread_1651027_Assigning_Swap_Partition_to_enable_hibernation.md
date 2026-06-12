---
title: "Assigning Swap Partition to enable hibernation"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by crazymao on 2010-12-22
i want to create/assign a swap partition so i can hibernate by comp. i've tried the ubuntu guide on creating a swap file but it didnt work, i created a linux-swap partition and used the mkswap command but that didnt work either (maybe it did but i cant hibernate anyway?!) right now my partitions look like this:

/dev/sda1      extended
  /dev/sda5    linux-swap
/dev/sda3      ntfs (windows partition)
/dev/sda4      ext4 (ubuntu partition)

any help/guide on how to do it would be appreciated, thanks :)

---

### Post by dabl on 2010-12-22
Let's see the output of

```
sudo mount
```

and also

```
sudo blkid
```

and also

```
cat /etc/fstab
```

---

### Post by plucky on 2010-12-22
And ```
cat /etc/initramfs-tools/conf.d/resume
```


Good Luck

---

