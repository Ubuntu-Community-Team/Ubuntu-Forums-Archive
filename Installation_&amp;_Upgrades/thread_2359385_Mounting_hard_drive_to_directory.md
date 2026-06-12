---
title: "Mounting hard drive to directory"
date: 2017-04-23
forum: Installation &amp; Upgrades
---

### Post by kalindimitrov on 2017-04-23
I want to make build with 2 ssd and 1 hard drive. I will use one ssd for boot/os one for home and I want to use hard drive just for two directories which must be placed in home.I don't have idea how to achieve this and don't know what to type to google it.
I hope there is a way to achieve this on installation. I will use ubuntu 17.04

---

### Post by SeijiSensei on 2017-04-23
Mount the drive to a separate directory, say /data, and use symbolic links to the two directories in your home directory.
```

sudo mkdir /data
sudo mount /dev/sdc1 /data
sudo chmod 777 /data -R
cd /home/username
ln -s /data/dir1
ln -s /data/dir2

```
You might want to consider more restrictive permissions on /data, or make it owned by your username:
```

sudo mkdir /data
sudo mount /dev/sdc1 /data
sudo chown username:username /data -R
sudo chmod 755 /data -R
cd /home/username
ln -s /data/dir1
ln -s /data/dir2

```
Here I'm assuming /dev/sdc is the drive you want to mount, with a single partition, /dev/sdc1. That depends on how the devices are named at boot.  You'll also want to add an entry to /etc/fstab to mount the drive whenever you reboot: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).  I recommend using UUIDs to designate devices.  To see the UUID for the mounted device, use the command "sudo blkid".  You'll get results that look like this:
```

/dev/sda1: UUID="a910ed52-d30b-4aba-9c21-bd474cc50df4" TYPE="ext2" 
/dev/sda5: UUID="795185b2-4c6d-4488-8ccc-42a08453a1d5" TYPE="ext4" 
/dev/sda6: UUID="852f0a01-d480-48b3-b100-520f23fc523e" TYPE="swap" 

```
Leave off the quotation marks in the /etc/fstab entry.

---

### Post by kalindimitrov on 2017-04-23
Thanks. But what will happen after reboot.Is it persistent ?
ops 
"
[COLOR=#000000]Here I'm assuming /dev/sdc is the drive you want to mount, with a single partition, /dev/sdc1. That depends on how the devices are named at boot. You'll also want to add an entry to /etc/fstab to mount the drive whenever you reboot: [/COLOR][https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
"
I read it too late

---

### Post by TheFu on 2017-04-23
If you put each mount into the /etc/fstab (using an editor to add the line(s) you need), then yes, it will be persistent.

I would never **chmod -R 777** on anything.
Also, instead of using symbolic links, you could mount the storage exactly where you want it under your home.  A "mount point" is really just an empty directory.  There are good reasons to do it with symlinks and there are good reasons to mount it directly where you want it.  Really just a judgment call.  For me, how I decided to do it would completely depend on how I was going to backup the system, the HOME and the data.  

How I backed it up would also be dependent on whether I needed online backups or if I needed image-based backups.  If I needed online backups, then I'd use LVM so snapshots can be used to ensure the backups aren't corrupted.  

I use LVM on all physical installations. It provides great flexibility and some great features. However, it is possible to be overly complex for someone new to Linux storage management.

You didn't ask, but I'd use GPT partitioning, not MBR, for a number of reasons.

---

### Post by SeijiSensei on 2017-04-23
> **TheFu said:**
> I would never **chmod -R 777** on anything.

On a single machine being used by a single person, I don't think there's much danger in using 777 permissions.

> Also, instead of using symbolic links, you could mount the storage exactly where you want it under your home.  A "mount point" is really just an empty directory.  There are good reasons to do it with symlinks and there are good reasons to mount it directly where you want it.

The OP wants to incorporate two directories from the larger device in his or her home.  To do that with mounting would require making two partitions, each storing the contents of one directory, and mounting them inside /home/username.  I suggested symlinks since the original plan was to have one mounted device with two directories.

---

