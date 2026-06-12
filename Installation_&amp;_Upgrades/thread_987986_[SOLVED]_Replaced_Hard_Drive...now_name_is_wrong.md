---
title: "[SOLVED] Replaced Hard Drive...now name is wrong"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by toddk111 on 2008-11-20
I just replaced a 1TB SATA hard drive.  I dual boot Linux & Vista.  My old drive/partition was NTFS and called New Volume.  So when I mounted it in Linux it appeared as "New Volume".  I physically removed that drive (it was full and I want to keep the data for now).  

I just put in a new 1TB SATA drive, booted to Vista and named it TD03.  When I rebooted into Linux, it automounted the drive and appeared on the desktop as TD03.  When I double-click on the desktop launcher for TD03, it appears as TD03 on the tree in the file browser but the "location" at the top of the file browser reads "/media/New Volume". 

I think it is confusing the old (now removed) hard drive with the new one.  What do I do to correct this problem?

Thanks,
Todd

---

### Post by __Ryan__ on 2008-11-20
I'm assuming you want it mounted at /media/TD03, if that's not the case change the name throughout the rest of the steps.

First create the new mount point:

```
sudo mkdir /media/TD03
```

Edit **/etc/fstab** and change '/media/New\ Volume' to '/media/TD03' in the entry for your new drive.

To make this effective immediately:

```
sudo umount /media/New\ Volume && sudo mount /media/TD03
```

Good Luck!

---

### Post by vanadium on 2008-11-20
There is no editing in /etc/fstab needed because currently, the drive probably is not mounted using /etc/fstab.

In my opinion this will be a rather harmless nautilus bug. I would not take any action if for the rest you can access and use the drive normally. Chances are the problem will be gone after rebooting.

---

### Post by toddk111 on 2008-11-21
> **__Ryan__ said:**
> I'm assuming you want it mounted at /media/TD03, if that's not the case change the name throughout the rest of the steps.

First create the new mount point:

```
sudo mkdir /media/TD03
```

Edit **/etc/fstab** and change '/media/New\ Volume' to '/media/TD03' in the entry for your new drive.

To make this effective immediately:

```
sudo umount /media/New\ Volume && sudo mount /media/TD03
```

Good Luck!

That fixed the problem.  Thanks!

---

