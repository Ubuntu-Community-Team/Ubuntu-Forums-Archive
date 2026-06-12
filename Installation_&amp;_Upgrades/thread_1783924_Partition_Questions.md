---
title: "Partition Questions"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by Squeeeee on 2011-06-16
Hi All

I'm a newbie, so please bear with me...

I have a HP Pavilion dv8000 series laptop that I wish to replace Windows XP with Ubuntu. I've created a load disc and started the installation process. I am looking at the advanced partitioning tool and a little confused on how to proceed. 

At the moment drive space looks like this...

 

Could you please advise the best way to set up my system?

Thanks!
Squeeeee

---

### Post by sanderd17 on 2011-06-16
I don't see your current configuration. But what config do you want? Do you want to separate your data from the OS? and are you sure you want to remove Windows already?

When I switched to Linux, I first needed about 6 months in a dual boot before I could fully switch.

---

### Post by Squeeeee on 2011-06-16
Sorry...Here is my configuration.

My windows OS became heavily infect by a virus and I don't have the original boot disc or key for it. So now I'm looking to salvage the laptop by wiping it and installing a new OS.

Device      Type     Mount Point     Format     Size          Used
/dev/sda
free space                                                  100030mg
/dev/sdb
free space                                                  100030mg

---

### Post by sanderd17 on 2011-06-16
You may want to place the output in CODE tags (click on the # in edit mode).

So you have a drive of about 200GB?

Then the best configuration is as follows:
[LIST]
[*]186 GB for /home
[*]12GB for /
[*]2 GB for swap
[/LIST]

So clear the current settings by saying "create new partition table" or something like that and then make those new partitions with their mount points.

If you don't find it, you can also go one step back and choose "use entire disk". This will create a root partition (/) and a swap partition. The home will be in the root partition.

---

### Post by Squeeeee on 2011-06-16
Thanks Sanderd17!

Just to clarify...I have two 100gb drives.

Will this affect the layout you suggested?

---

### Post by sanderd17 on 2011-06-16
Yest, that affects my layout since you cannot split /home over two drives. Is there a directory that contains lots of files?

Like are you a music or a video person? In that case, you could pick 86 GB for /home and leave the HDD of 100 empty at first and later on use it as /home/username/music or so.

Does that sounds ok?

---

### Post by Squeeeee on 2011-06-16
Thanks Sanderd17!!!

You've saved my POS laptop. 

At least until I run into something else I don't know how to fix. :)

I'm looking forward to using Ubuntu.

---

