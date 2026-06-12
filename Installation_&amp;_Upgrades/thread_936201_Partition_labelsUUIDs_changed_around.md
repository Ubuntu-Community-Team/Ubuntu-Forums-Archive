---
title: "Partition labels/UUIDs changed around"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by larryni on 2008-10-02
A few weeks ago re-partitioned the hard drive of my laptop as follows:

```
sda1 - / Ubuntu
sda2 - / for test install
sda3 - extended
       sda5 - swap
       sda6 - /home Ubuntu
       sda7 - /home for test install
       sda8 - storage for media accessible by either install
```

I installed Hardy using sda1, sda5, sda6 and sda8.

Then I decided to try out OpenSuse 11 and install it using sda2, sda5, sda7. When it came to chose the partitions I noticed that sda7 and sda8 had suddenly swapped labels, ie sda7 was now sda8 and vice-versa. I quit the installer and booted back into Ubuntu to make sure things were still working as they should, fired up Gparted and yes, the labels had changed. I checked the fstab entry for sda8:

```
# /dev/sda8
UUID=0a5e490d-da61-4f63-8417-bd0bb945da12 /media/media    ext3    relatime        0       2
```

I checked out the UUID and instead of sda8 it's the one for sda7. So now my partition setup was as follows:

```
sda1 - / Ubuntu
sda2 - / for test install
sda3 - extended
       sda5 - swap
       sda6 - /home Ubuntu
       **sda8** - /home for test install
       **sda7** - storage for media accessible by either install
```

I left it like that and went ahead with the OpenSuse install using sa2, sda5, and sda8. No problem with the install.

A couple of days ago I was playing around with a new conky setup in Ubuntu and decided to display the memory usage, including swap. To my surprise it showed up as 'no swap'. I rebooted - still no swap. 

I tried ```
sudo swapon -a
``` and it gave an error message that the UUID in fstab could not be resolved (can't remember the exact message). The sda5 UUID had changed as well. It was easily fixed by editing fstab and replacing the UUID with /dev/sda5. But I'm still not sure when or how the UUID changed.

Any idea what's going on here?

---

### Post by dabl on 2008-10-02
I haven't used Suse, but I know that a reformat will change the UUID of a partition -- I wonder if Suse is formatting while installing.

---

### Post by larryni on 2008-10-02
> **dabl said:**
> I haven't used Suse, but I know that a reformat will change the UUID of a partition -- I wonder if Suse is formatting while installing.

I thought that might be the case. Does an existing swap partition usually get formatted when installing a distro? Would it be best to use separate swap partitions when dual booting?

---

### Post by cariboo on 2008-10-02
I use the same swap for Hardy and Intrepid, Every time I install a newer version of Intrepid the swap partition gets formatted. They have fixed the problem of partitions changing device numbers in Intrepid which will be out at the end of the month.

Jim

---

### Post by larryni on 2008-10-03
That's good to know, I was going to install the Intrepid beta later on.

I still wonder though how sda7 and sda8 changed around, this had nothing to do with OpenSuse as far as I can see.

---

