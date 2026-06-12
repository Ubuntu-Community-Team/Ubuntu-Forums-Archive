---
title: "Partition Scheme Suggestions for SSD + HDD dual boot"
date: 2019-01-04
forum: Installation &amp; Upgrades
---

### Post by Deleted20200712 on 2019-01-04
I have recently ordered a laptop (2019 Dell Inspiron Business Laptop (Windows 10 Professional, AMD Quad-Core A12-9700P up to 3.4GHz Processor, 15.6" HD (1366 x 768) Truelife LED Display, 1TB HDD + 256GB SSD, RAM: 16GB DDR4)) which comes with both an HDD and an SSD.

I will be removing the existing Windows 10 installation and replacing it with a vanilla Windows 10 installation (only for a few programs for which there is no Linux version; I don't like using WINE and when I try to use these programs in a VM there are always issues, so unfortunately I have to use Windows for them).

My main OS will be Ubuntu (as it always is).  I'll be using 18.04 (I only ever use LTS these days).  I will be mostly using it for gaming (nothing too resource intensive, and I'll put the settings on their lowest anyway; I mostly play Dota2 but now that I'll have a better computer than what I'm currently using, I want to try out some other games in my rather large Steam library).

So I would like to know what would be the best partition scheme.  Which folders should go on the SSD and which on the HDD?  I was going to put the Windows installation and the swap on the HDD.  I plan to put / on the SSD and /home on the HDD, but what about others, like /opt, /var, /tmp, and everything else?  Does anyone have any recommendations?  What about sizes for each?  I've done some googling and come up with conflicting advice.

Thank you in advance.

---

### Post by oldfred on 2019-01-05
Ubuntu standard desktop install is now just / (root). It uses a swap file.
If an UEFI install it also will want an ESP - efi system partition which is the FAT32 with boot flag.
I prefer to keep /home inside / since it really is small. Just hidden files with settings and a few apps like Thunderbird & Firefox profiles (which I also move to HDD).

I would not put any other system folders into partitions. And I mount /tmp to RAM, if you have enough RAM.

But each user has to decide, my own optimal partitioning plan from several years ago now needs adjusting.
Are you going to install other flavors of Ubuntu to test, or another / partition just to experiment with settings to make sure you do not corrupt main working install.
Do you have lots of media files, and want those in separate partitions?
But too many partitions can create issues where one fills up and another has lots of space. So some trade-offs.

---

### Post by Impavidus on 2019-01-05
What are your needs? How much space do you need for your documents? A separate partition for /home or just your documents is a good idea. Putting /tmp in RAM is reasonable too. Other partitions for OS stuff just makes things more complicated.

---

### Post by CatKiller on 2019-01-05
> **jasonmallet said:**
> I plan to put / on the SSD
Good. 
>  and /home on the HDD, 
Good. 
> but what about others, like /opt, /var, /tmp, and everything else?
Don't.

It's hassle for no benefit, and a pain when you discover that the sizes you picked aren't appropriate for your needs. The only benefit comes when those are on a different machine, or using a different filesystem specifically optimised for the specific access pattern.

**If** you have too much RAM and you want to reduce writes to your SSD, mounting /tmp as a ramdisk will do that. Even that's not really worth it, since SSDs have got to the point that you'll upgrade to a bigger one before you run out of writes.

Your Home folder will contain your settings, and likely any music, videos, and Steam games you have. Well suited to bulk storage on a HDD. However much you don't need for the Windows install on that drive you can have for /home.

---

