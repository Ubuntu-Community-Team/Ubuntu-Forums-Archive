---
title: "Copying into a Linux partition from a LiveCD"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by mbslrm on 2009-12-30
How can I mount a partition in the LiveCD with write privileges?

Thanks in advance!

---

### Post by pytheas22 on 2009-12-30
Open a terminal in the live session and type:
```

sudo nautilus
```

This will open up the file browser as root.  See if you can copy your files that way.

If this doesn't help, you may need to mount the partition from the terminal.  To do that, you would need first to create a mountpoint:
```

sudo mkdir /mnt/mountpoint1
```

Then mount the partition with a command like:
```

sudo mount /dev/**sda1** /mnt/mountpoint1
```

Note that the part in bold might be different for you, depending on how many hard disks you have and how their partitions are configured.  In general, sda1 means the first partition (#1) of the first hard disk (sda); sda2 would be the second partition of the first hard disk; sdb1 would be first partition of the second hard disk, etc.

Once the partition is mounted, open a file browser as root (using the command "sudo nautilus", as above), then browse to the location /mnt/mountpoint1 and you should see the files.

Also note that you can name the mountpoint whatever you want; /mnt/mountpoint1 is just an example, but /mnt/anything-else would also be valid.

---

### Post by mbslrm on 2009-12-30
Thank you very much!

---

