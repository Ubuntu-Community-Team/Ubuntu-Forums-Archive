---
title: "Installation to an SSD"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by irishcherioladd on 2011-01-23
I bought a Samsung N150 Plus for Christmas, and have bought a SSD for it. I have some concerns. 

1) As it is a netbook (light use: email, music, facebook), which filesystem do I want to use? I've seen things like avoiding ext4 but I'm not sure. 

2) Anything I need to worry about after installation to preserve lifespan?

3) Are there any other tweaks I can try to minimize my boot time?

Thanks ahead of time!

---

### Post by efflandt on 2011-01-23
If your SSD does TRIM, I think that only works for ext4, but you can disable the ext4 journal to eliminate the extra writing for that.  If your SSD does not do TRIM, you might as well use ext2 (like ext3 without journal).  Just avoid pulling the plug if running with the battery removed (my desktop has a UPS), but even that should not be a problem unless writing to the drive at the time.

```
sudo tune2fs -O ^has_journal /dev/sda1 (substutute your partition for sda1)
```In /etc/fstab you need to add the discard option to do trim, and I also added noatime, so it does not write every time a file is accessed.  I also use tmpfs for /tmp.

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e70810eb-379d-4f9f-9087-54c2f1cd96f9 /    ext4    noatime,discard,errors=remount-ro 0       1
tmpfs        /tmp        tmpfs    nodev,nosuid    0    0
```I have no swap because it is a desktop w/8 GB RAM,  but if you use swap on the SSD, you may want to set swappiness to a low value like 10 or 1 to minimized swap.  Swap at least as large as RAM is needed if you want to hibernate (not necessary for suspend).

---

### Post by snowpine on 2011-01-23
ext4 is my recommendation (don't use ext2 because if your battery runs down you're in trouble) and no special precautions are necessary. Modern SSDs are designed to last for many years under normal everyday use.

---

### Post by irishcherioladd on 2011-01-23
So I'd need 2GB of swap for 1GB of RAM?

And isn't there a faster file system?

---

### Post by snowpine on 2011-01-23
> **irishcherioladd said:**
> So I'd need 2GB of swap for 1GB of RAM?

And isn't there a faster file system?

There is no one-size-fits-all answer for swap. If you don't hibernate and never use up all of your RAM, you may not need swap at all. I have two netbooks, each with 1gb of RAM. One of them has a 160gb HDD, so I use 2gb of swap, but the other only has an 8gb SSD, so I don't have swap at all.

ext4 is the latest and fastest filesystem in the ext series. There is a supposedly faster filesystem called btrfs ("better file system") under development, but it is not yet stable for use.

---

### Post by irishcherioladd on 2011-01-23
btrfs was the one I had heard of. Thanks for clearing that up. 

And the SSD I'm getting has 60GB, so I think I can spare a bit for for a swap, just for giggles.

---

### Post by snowpine on 2011-01-23
I stand corrected, actually you can use btrfs in Ubuntu 10.10. I can't vouch for this information personally, but here you go: [https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

---

### Post by irishcherioladd on 2011-01-23
> Do a regular installation except use manual partitioning to create:

a ext2 or ext3 partition of about 250MB for /boot
a btrfs partition for /
a linux swap partition large enough to allow for suspending to RAM (amount of ram plus 100MB is a good size) If you don't need suspend support then not more than 2GB is sufficent.

It seems easy enough, but do I want to?

---

### Post by snowpine on 2011-01-23
> **irishcherioladd said:**
> It seems easy enough, but do I want to?

I haven't tried it personally. My recommendation is ext4 as I stated above.

You can use the forum Search feature to read existing discussion threads about btrfs. :)

---

### Post by irishcherioladd on 2011-01-23
Also, I did some more researching and I found NILFS and ZFS. Any experience?

---

