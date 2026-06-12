---
title: "Partition Scheme for 2TB NVMe SSD with Multiple Ubuntu OS Versions?"
date: 2023-11-12
forum: Installation &amp; Upgrades
---

### Post by theassociate on 2023-11-12
Have a ZBook Fury 17 G8 workstation laptop with two 2TB NVMe SSDs. Both are unformatted/empty. 

Was going to duplicate what I did on a previous laptop where I used GParted to create three separate partitions (for different Ubuntu OS installations) on a 512GB SDD and then created a single partition for HOME on a separate 1TB HDD. 

Just wondering what my partition scheme should look like on this newer machine with its two much larger capacity NVMe SSDs. Should I use the same partition scheme again with the two drives, only increasing the size of each OS partition on the first drive to take advantage of the extra space...

OR

Should I just install my partitions for  /boot, multiple /roots, and /home all on one NVMe SSD, using the entire second NVMe for dedicated storage/backup?

For reference, I've attached the partition scheme I used for my old laptop (ignore the EFI partition on /dev/sdb). Would obviously tweak partition sizes, increasing /boot to a gig or more and making each Ubuntu OS partition 100GB or so.

Oh, and would I even need swap if I have 80GB of RAM? If so, how much?

Thanks much. Be blessed today.

---

### Post by Impavidus on 2023-11-12
If you want a /boot partition, you can create one. There are few scenarios where you actually need one. /boot can't be safely shared among multiple installed systems.

There's no /root partition. There's a / partition, also known as a root partition. /root is the home directory of the root user and must be on the root partition. How large you should make your root partitions depends on your needs. Mine is 32GB and is only half full. You have room to spare. 30GB should be sufficient, 50GB won't hurt. The demands slowly increase.

Don't share one /home partition among multiple installed systems, unless you use a different username on each of them. Your home directory is where your config files get stored. Different versions of the OS may store incompatible versions of config files at the same location, breaking applications.

The default today is to use a swap file, not a swap partition. But with multiple installed systems, a swap partition is easier to share. You can't share swap if you use hibernation, but hibernation isn't really recommended anyway (and normally disabled). It's unlikely you'll ever use swap, but having some may enable some optimisations. You can set it to 4.1GiB, if you want a number.

I suggest a big shared data partition. Using the second drive for backups may be nice, but keep in mind that a proper backup is external. Even better, off site.

---

### Post by theassociate on 2023-11-12
Good thoughts, Impavidus. And yes, of course about /. Duh. 59-year-old brain fart.

So, what if I just scrap the idea of multiple Ubuntu OSes and go with a more traditional four-partition set-up (/boot, /, swap, /home) on the first 2TB NVMe, which still allows me to clean-install a future Ubuntu flavor over my existing OS without having to touch /home when the time comes?

Thing is, gone are my days of triple-booting Windows, OSX, and Ubuntu, as I've been using Ubuntu exclusively going on three years now. In addition, I really don't need to be accumulating multiple Ubuntu OSes moving forward. I rarely touch the old releases after I upgrade anyway. 

So, if I go with a more straight-forward partition scheme, what to do with the other NVMe drive? Just make it /data storage?

So as not to complicate things further, I withheld from mentioning that I also have an unformatted 1TB SATA SSD in my Fury. Don't see myself having much use for it since I've already got two brand-spankin' new 2TB Samsung 980 Pros.

Essentially, I'm wondering the best way to partition all this space, as honestly, I've never had the luxury before.

Incidentally, I'm not opposed to letting my Ubuntu USB Installer do a good ole' standard installation, just as long as this installation takes advantage of the entire first drive's space capacity and not just part of it.  

Thanks so much for your time. Blessings.

---

### Post by theassociate on 2023-11-12
> **Impavidus said:**
> I suggest a big shared data partition. Using the second drive for backups may be nice, but keep in mind that a proper backup is external. Even better, off site.

Love this idea, but admittedly, I'm not sure how to do it. Will investigate, though. Sure do appreciate the input. Thanks much.

---

### Post by Impavidus on 2023-11-13
> **theassociate said:**
> 
So, what if I just scrap the idea of multiple Ubuntu OSes and go with a more traditional four-partition set-up (/boot, /, swap, /home) on the first 2TB NVMe, which still allows me to clean-install a future Ubuntu flavor over my existing OS without having to touch /home when the time comes?That would work. A separate /home allows you to clean-install Ubuntu or any flavour while keeping your /home. The only case where I expect tat to fail is if you downgrade your Ubuntu version.

Note that a /boot partition has some uses (in particular, if your root filesystem is om some storage that grub doesn't understand), but most users don't need one. Similarly, some people like a separate /var or /opt or /usr/local. I suggest you only do such things if you've a specific reason.

> So, if I go with a more straight-forward partition scheme, what to do with the other NVMe drive? Just make it /data storage?Whatever you like. In my experience, computers are obsolete before the harddrive is full and you get a new and even bigger harddrive packaged with a new computer, so I always leave large parts of it unused. I suggest you don't violate the [Filesystem Hierarchy Standard]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"). On Ubuntu, /bin, /sbin and /lib have been replaced by symlinks to /usr/bin, /usr/sbin and /usr/lib, so a separate partition for /usr doesn't work anymore, if you even wanted that. But there's a way to avoid that, if you really wish.

> Incidentally, I'm not opposed to letting my Ubuntu USB Installer do a good ole' standard installation, just as long as this installation takes advantage of the entire first drive's space capacity and not just part of it.Doing everything automatically may not give exactly what you want on multiple drive systems.

---

