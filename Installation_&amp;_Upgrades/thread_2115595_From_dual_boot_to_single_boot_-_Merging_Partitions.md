---
title: "From dual boot to single boot - Merging Partitions"
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by am_i_registered on 2013-02-13
Hello all,

I am proud to announce that I'm ready to entirely discard MS Windows.

Back on 2008, I decided to go dual boot, mostly because I got tired of MS Windows crashes.
The migration process was difficult and long (4years), but I don't regret about any single moment of it.

The question now is what software to use in order to delete the Windows 7 partition and merge the resulting unallocated space to the existing Ubuntu 12.10 partition. 
I could use the LiveUSB version of Ubuntu 12.10 to boot and then use GParted to do the job, but for some weird reason GParted hangs at "Scanning all devices..."

I didn't have this problem before... any help?

---

### Post by schragge on 2013-02-13
What partitioning scheme do you use for your Ubuntu installation? Now, that you have a spare partition, instead of merging you can e.g. put your /home in it.

---

### Post by oldfred on 2013-02-13
I also prefer smaller system partitions of 10-25GB depending on how large hard drive is and space you want for Ubuntu. You can use the separate /home or just reformat partition to use as data and link folders back into your system so it is invisible as separate partition.

Long time ago I had issues with gparted not seeing my sda drive at all. It took a real long time and then showed other drives. But issue was my XP install needed chkdsk even though it booted. After chkdsk gparted showed sda right away and XP even booted a bit faster.

Post this

       sudo parted /dev/sda unit s print

---

### Post by am_i_registered on 2013-02-13
> **schragge said:**
> What partitioning scheme do you use for your Ubuntu installation? Now, that you have a spare partition, instead of merging you can e.g. put your /home in it.

Thanks for the advice. I already use a separate HDD for my /home directory.

the ```
sudo parted /dev/sda unit s print
```command gives the following:

Model: ATA ST31500341AS (scsi)
Disk /dev/sda: 2930277168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start        End          Size         Type     File system     Flags
 1      2048s        2913499135s  2913497088s  primary  ext4            boot
 3      2913499136s  2930276351s  16777216s    primary  linux-swap(v1)

---

### Post by am_i_registered on 2013-02-13
hmmmm....

I found an old LiveUSB stick with Ubuntu 11.04 natty and booted from there...
GParted did the jobs pretty fast and easy..

Thanks for your answers anyway!

---

