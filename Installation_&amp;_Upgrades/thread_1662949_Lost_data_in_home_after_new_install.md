---
title: "Lost data in /home after new install"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by landsg on 2011-01-08
Hello All:

I just installed Ubuntu 10.10 from 9.04.  I already had a separate partition for my /home directory, and was careful not to reformat that during the install.  I tagged it as /home during install. 

When I booted up to 10.10, there is nothing in my /home directory.  All of the normal folders are there (i.e music, pictures, video), but none of my old data.  Below is  the output from running fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=63cd9c37-0a0c-4ba9-bf41-1cf1e68dcc1a none            swap    sw              0       0

Can I used G-Parted to correctly mount the old home directory?   Thanks in advance for your assistance!

---

### Post by Bucky Ball on 2011-01-08
Are you saying you now have two /homes? Old and new? One in the new install which is a folder and one which is a partition (which is visible in your output)?

---

### Post by landsg on 2011-01-08
Thanks for the reply.  No, only one /home shows up when I run G-Parted.  However, it's about 2 .39 gig in size, which makes me think my old data is still there but I just can't see it.

---

### Post by landsg on 2011-01-08
Here is fdisk output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24837113

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       19457   146520802    5  Extended
/dev/sda5            1217       19088   143556808+  83  Linux
/dev/sda6           19089

---

### Post by Bucky Ball on 2011-01-08
Hmm. How about the output from:

```
sudo blkid
```

---

### Post by landsg on 2011-01-08
> **Bucky Ball said:**
> Hmm. How about the output from:

```
sudo blkid
```

/dev/sda1: UUID="6ac7c078-784c-4096-8571-9259dbb026c9" TYPE="ext3" 
/dev/sda5: UUID="182ce36f-0550-4432-9190-3759ee164875" TYPE="ext3" 
/dev/sda6: UUID="63cd9c37-0a0c-4ba9-bf41-1cf1e68dcc1a" TYPE="swap"

---

### Post by Bucky Ball on 2011-01-08
Try this:

```
sudo mount /dev/sda5
```

... but probably already mounted by the looks.

---

### Post by landsg on 2011-01-08
mount: /dev/sda5 already mounted or /home busy
mount: according to mtab, /dev/sda5 is already mounted on /home

---

### Post by md_jk on 2011-01-15
same problem here!
I did a clean  install of Ubuntu Maverick over an old lucid , I had a separate home partition so i thought the files on this partition would not be affected.  However after install completed , i found lost and found folder on the old home partition ( have no access to this folder ) but it seems to be empty , together with  a new home directory (now 24gb in size 
My home partition is 125GB but only 80 GB is free thus a  deficit of 20gb,that i cannot seem to find


My laptop is toshiba satellite c-650

---

