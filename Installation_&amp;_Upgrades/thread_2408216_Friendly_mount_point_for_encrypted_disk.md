---
title: "Friendly mount point for encrypted disk?"
date: 2018-12-15
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2018-12-15
I have an crypto_LUKS volume on sdb1, and I can mount it fine, but it mounts to /media/username/longUUIDcode which is messy.

Can I edit /etc/fstab in such a way, that when I manually access and unencrypt this disk from Nautilus (which works fine), that it will neatly mount to either /media/mountname /mnt/mountname?

I got the UUID with sudo blkid, mkdir /media/.net, and then added the following line to fstab, but I could not boot after this so I commented it out so I could log back in:

```
UUID=longUUIDcode /media/.net    ext4    defaults    0     1

```

Just to be clear, I would not like this volume automounted on boot - only when I manually mount it via nautilus, I would like it to mount to somewhere like /media/mountname.

Also, when it is mounted, I am unable to create any files, is there a command to correct ownership please?

---

### Post by TheFu on 2018-12-16
I don't use GUIs for mounting. Too many issues - and often terrible performance.
The fstab is the easiest, but you can use **autofs** which would only mount the file system when requested. I don't know if autofs handles LUKS in a nice way or not.

File and directory permissions are core to all Unix-like OSes.  It is a basic skill to learn and you should learn it sooner than later to avoid hours, days, weeks, months of frustration. Any Unix permissions tutorial will teach what you need to know.  chown/chmod are the normal commands.

---

### Post by Dáire Fagan on 2018-12-16
Thanks for the reply.

I resolved this with the following steps:

```
sudo apt install cryptsetup-bin
sudo cryptsetup luksFormat /dev/sdb1
```

Then after mounting the partition in Nautilus, in the Disks utility I selected the 'unknown' partition on the drive, selected the cog icon for settings, and formatted it to ext4 inputting a friendly volume name.

Now whenever I mount the partition, it automatically mounts to /media/username/friendlyname.

---

### Post by TheFu on 2018-12-16
And the permissions issues?  I don't see anything in the last post which would handle them.

---

### Post by Dáire Fagan on 2018-12-17
> **TheFu said:**
> And the permissions issues?  I don't see anything in the last post which would handle them.

I can see in my terminal history at one point I input:

```
sudo chown dusf:dusf /media/dusf/friendlymountname -R
```

Though this may have been before I entered the commands in my last post, and may not be necessary after they are input.

---

