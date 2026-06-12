---
title: "Best partition method for future updates?"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by 9littlebees on 2012-11-18
Hi all, I'm a relative Linux newbie, and am currently dual-booting Win7 with  Xubuntu 12.10.

However, I am aware that in 6 months time, a new version will come around which I will probably want to upgrade to.  This is where my question comes in... What is the optimum partitioning method for upgrading the distro?

Currently I have my partitions arranged thus:

**sda (120GB SSD)**
sda1: NTFS Win7 install (80GB)
sda2: /boot (200MB)
sda3: swap (2GB)
sda4: / (30GB)

**sdc (500GB HDD)**
sdc1: NTFS Win games (200GB)
sdc2: NTFS Win user area (200GB)
sdc3: /usr (40GB)
sdc4: /home (30GB)

I'd be quite interested in knowing of the best arrangement for upgrading, and why.  I could happily change my 30GB root partition to be extended and include /tmp and /var as separate partitions.  Would this be useful, though?

Oh, and this is for a powerful desktop rig running:

[LIST]
[*]i5 2500k 3.3GHz CPU
[*]16GB RAM
[*]Radeon HD 6870 graphics card
[*]120GB SSD
[*]500GB HDD
[*]1TB HDD (used solely for storing photographs)
[/LIST]

---

### Post by snowpine on 2012-11-18
When you upgrade, your partitions will not be changed in any way, therefore your current scheme is fine. :) Your /home looks small but I assume that's because your photos and documents are on the shared partition with windows.

---

### Post by 9littlebees on 2012-11-18
> **snowpine said:**
> When you upgrade, your partitions will not be changed in any way, therefore your current scheme is fine. :) Your /home looks small but I assume that's because your photos and documents are on the shared partition with windows.

Oh wow, really? So when Xubuntu 13.04 is released, how would I upgrade to it? I thought I'd have to download the ISO and do a normal install...

---

### Post by snowpine on 2012-11-18
Wondering if you've see this page? (first Google hit for "upgrade Ubuntu")

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

---

### Post by 9littlebees on 2012-11-18
**> **snowpine said:**
> Wondering if you've see this page? (first Google hit for "upgrade Ubuntu")

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

Ah, that answers my question nicely. 

Also, yes I will be sharing personal documents with Windows. Do I need so much space in /usr or could I reduce it safely to something smaller?

---

### Post by oldfred on 2012-11-18
I have not broken out system partitions since my first install of Redhat 5 12 years ago and I was very confused about sizes. It really is more for servers and then the use of the server.

       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

    

My 64GB SSD has two Ubuntu system partitions including /home. But I have all data in either a NTFS shared or ext3 data partition on my rotating drive. I also have swap on the rotating drive just to have some but find I almost never use it with 4GB of RAM. The only reason my /home is 2GB in my working install is the Windows version of Picasa is still in .wine in /home. My total install with /home in my working install is about 9GB.

```
fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G  8.7G   18G  34% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M  1.0M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  128K  2.0G   1% /run/shm
/dev/sdc2       100G   32G   68G  32% /mnt/shared
/dev/sdc6        97G   44G   48G  48% /mnt/data
/dev/sdd4        28G  4.4G   22G  17% /media/Quantal

```

---

### Post by 9littlebees on 2012-11-18
Thanks for the advice and the link, oldfred. That makes good sense to me. I think I will just install Xubuntu to a single root partition and then place my /home drive on a second. 

I'm marking this thread as solved.

Thanks again, snowpine and oldfred!

---

### Post by snowpine on 2012-11-18
Sorry I didn't see this until now, but yes, oldfred's advice is sound, and your idea is a good one. But if you are happy with your current partitions there is certainly no need to reinstall with a different scheme.

---

### Post by 9littlebees on 2012-11-19
> **snowpine said:**
> Sorry I didn't see this until now, but yes, oldfred's advice is sound, and your idea is a good one. But if you are happy with your current partitions there is certainly no need to reinstall with a different scheme.
Ironically, after taking on your guys great advice, I couldn't help but tinker with my partitions and in the process wiped my Windows D drive.  :(

I'll now be reinstalling both OSes from scratch and have raised a new thread with my proposed layout and some questions:

[http://ubuntuforums.org/showthread.php?p=12362477](http://ubuntuforums.org/showthread.php?p=12362477)

---

