---
title: "Problems with 2 updates"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by antbully on 2008-05-27
Hello,

I'm having a problem upgrading two packages:

  linux-image-2.6.22-14-generic
  linux-restricted-modules-2.6.22-14-generic

What happens is I click the icon for Update Manager and try updating all packages.  The above two are the only ones that fail; here is the failure message:

```
E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_amd64.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/linux-restricted-modules-2.6.22-14-generic_2.6.22.4-14.10_amd64.deb: failed in buffer_write(fd) (10, ret=-1)

```

I thought the issue might be a /var partition that was too small, so I moved /var/cache/apt/archives to another very large partition (>60 GB) and soft-linked back to the location in /var.  Still this fails to install with the same problem.  The buffer_write(fd) thing looks like a partition is full somewhere, though.  What's going on?  What's the fix?

Thanks for the help,

antbully
(gutsy gibbon with updates...)

---

### Post by iaculallad on 2008-05-27
Try running the command in your terminal then redo the update.

Code:

> sudo apt-get install util-linux

---

### Post by antbully on 2008-05-27
I assume you meant I should do "sudo apt-get install util-linux".  This tells me

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
util-linux is already the newest version.
The following packages were automatically installed and are no longer required:
  torcs-data torcs-data-tracks torcs-data-cars plib1.8.4c2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


Er, what next?  I'm clueless with apt...

Thanks,

antbully

---

### Post by iaculallad on 2008-05-27
> **antbully said:**
> I assume you meant I should do "sudo apt-get install util-linux".  This tells me



Er, what next?  I'm clueless with apt...

Thanks,

antbully

On the terminal:

```
sudo apt-get clean
```

then redo your upgrade.

---

### Post by antbully on 2008-05-29
Ok, I did "sudo apt-get clean", and I understand it clears out the archive of downloaded packages.  However, redoing the upgrade yields the same message:
```
E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_amd64.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/linux-restricted-modules-2.6.22-14-generic_2.6.22.4-14.10_amd64.deb: failed in buffer_write(fd) (10, ret=-1)

```
:confused:

So I am confused.  Any help appreciated.

antbully

---

### Post by iaculallad on 2008-05-29
Try removing some of the older linux-images on your system (you can use synaptics). Then redo your update.

---

### Post by antbully on 2008-06-05
> **iaculallad said:**
> Try removing some of the older linux-images on your system (you can use synaptics). Then redo your update.

Hmmm. Well I don't know specifically how to use synaptics to do this, but from what I can see, it looks like the only linux images I have installed are linux-image-generic (very small) and linux-image-2.6.22-14-generic (the kernel, etc.).  Looking under /boot, I only see evidence of one installed kernel.

I believe have my system partitioned sensibly, but perhaps wiser eyes can see my error:
```
/dev/sda2     ext3      194449    166077     18332  91% /
varrun       tmpfs     1031688       236   1031452   1% /var/run
varlock      tmpfs     1031688         0   1031688   0% /var/lock
udev         tmpfs     1031688       132   1031556   1% /dev
devshm       tmpfs     1031688         0   1031688   0% /dev/shm
/dev/sda1     ext2       82769     19153     59200  25% /boot
/dev/sda8     ext3     4814936    140772   4429576   4% /home
/dev/sda6     ext3      194442      5820    178583   4% /tmp
/dev/sda5     ext3    10578780   3532696   6508712  36% /usr
/dev/sda7     ext3     1976492    273272   1602816  15% /var

```

I'm about resigned to this now, but it would be nice to figure it out...

Thanks,

antbully

---

### Post by Sef on 2008-06-05
Are you running the 64-bit version of Gutsy Gibbon?

---

### Post by antbully on 2008-06-06
> **Sef said:**
> Are you running the 64-bit version of Gutsy Gibbon?

I believe so:
```
uname -a
Linux splitbrain 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
```

---

