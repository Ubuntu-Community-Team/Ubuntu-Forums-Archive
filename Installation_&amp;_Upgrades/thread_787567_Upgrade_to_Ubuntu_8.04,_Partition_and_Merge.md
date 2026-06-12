---
title: "Upgrade to Ubuntu 8.04, Partition and Merge"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by Verminox on 2008-05-09
Hello. I need some help in upgrading my Kubuntu 6.06 LTS to Ubuntu 8.04 LTS. 

**What I currently have** (Checking using Windows Disk Management)
[LIST=1]
[*] 30GB NTFS (Windows XP)
[*] 10GB FAT32 (Shared)
[*] 35GB Unknown (Kubuntu 6.06)
[*] 2 GB Unknown (Guessing its the swap partition, I'm not sure)
[/LIST]

**What I would like to have**
[LIST=1]
[*] 30GB NTFS (Windows XP)
[*] **30GB** FAT32 (Shared)
[*] 15GB **Ubuntu 8.04**
[*] 2 GB Swap
[/LIST]

**What should be done**
I have read the [Upgrading to Ubuntu 8.04]("http://www.ubuntu.com/getubuntu/upgrading") documentation but I don't want to upgrade through software because I already have the installation CD. 

Furthermore, it says that there is an option to upgrade even on the CD, but I don't know whether this works to upgrade from Kubuntu to Ubuntu.

Also, as you can see from the list above, I want to downsize the Linux partition and transfer 20GB of space to the shared FAT32 drive (so that I store my media there for both OSes to read without requiring any additional software). Is it possible to bring about this merge while the FAT32 partition contains data (current state) ? Or will I have to make a separate FAT32 partition without touching the original one?

One more thing: I read that I would need to use fixmbr if I uninstalled Kubuntu and wanted to use only Windows, but in my case I will be uninstalling Kubuntu 6.06 and installing Ubuntu 8.04 while the LiveCD is in, so am I right in assuming that I won't need fixmbr?

---

### Post by Verminox on 2008-05-09
Ok so I've burned the LiveCD and I rebooted into it, then opened GParted. I can see this:

/dev/sda1 - NTFS
/dev/sda2 - Extended (locked)
-- /dev/sda5 - FAT32
-- /dev/sda6 - Linux Swap (locked)
/dev/sda3 - ext3

Now, I am able to delete the ext3 partition, but I want to also delete the swap partition so that I can move some space into the FAT32. But I can't do that because that partition is locked! How do I unlock it?


PS: I'm thinking of just deleting ext3, swap... resizing the FAT32, and then proceeding with installation as normal. No fixmbr or anything. Am I correct?

---

### Post by Verminox on 2008-05-10
Errmmmm... can anybody help me out here?

---

