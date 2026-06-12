---
title: "2nd drive ~ how to"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by PrvSAT on 2010-01-06
Hello friends,

I successfully installed ubuntu on one drive in two partitions, one for the OS and one for storage! Victory!!!

Now I wish to add the second drive (2nd sata). If I leave the drive unpartitioned, will ubuntu see it and ask me to partition it, like any plug and play? Or how should I proceed to add the second drive (currently in ntfs but wish to be EX4 or3) safely, please? I am afraid to not screw up anything what is on the first drive.

Thank you for reading this message. :)

---

### Post by captain_171 on 2010-01-06
Hi,
You will need to use gparted to partition that drive.
When you open gparted you will see on the left site a pull down menu select the drive that does not have any file systems on it. To tell if that drive has any file systems click on the drive on the left pull down menu and then look on the lower white area if there is any thing that says /boot or / do not use that drive.

To partition your new drive.
Go into gparted and select the new drive you wish to use and select the gray unallocated area and then select new. at this point you can select what file system to use such as EXT3 or EXT4 or FAT32 and then enter a label and click add
and after that click apply.

To open gparted press alt - F2 and type in: 
gksu /usr/sbin/gparted

Please backup any data before using gparted just in case.

---

### Post by PrvSAT on 2010-01-06
Thank you for the quick reply and help captain! :)

It must work because I do not have anymore space for backup for now until I will add this drive.

---

### Post by Bartender on 2010-01-06
If you plug it in, then start Ubuntu, I don't think it will auto-mount the second drive, but it will see it if you go into Places>Computer.  Ubuntu can read drives with the NTFS file system.

If you're sure you're going to use it with Ubuntu exclusively, then you may want to re-format it as described above to avoid fragmentation.

I know it's not hard to identify the drive and add a line to the fstab file so that it's mounted at start-up, but I haven't messed with fstab lately.

---

### Post by PrvSAT on 2010-01-06
> **Bartender said:**
> 
I know it's not hard to identify the drive and add a line to the fstab file so that it's mounted at start-up, but I haven't messed with fstab lately.

Thank you Bartender,
Of course I want the drive to be ready to read and write after boot up. I have no idea what fstab is. I am able to open a terminal and type whatever is required but I need help what to type in... LOL
I thought that the drive once formated will mount automatically after boot up. If not, what could I do to "fix" this, please?

---

