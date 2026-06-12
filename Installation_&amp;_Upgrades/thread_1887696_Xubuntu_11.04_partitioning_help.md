---
title: "Xubuntu 11.04 partitioning help"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by bosler on 2011-11-27
So, about three months ago, I got the notion that I should build my own computer just as a learning process. I've finally hammered out all (I hope) of the hardware issues, and am now trying to install Xubuntu onto a 20 GB Hard Drive that I've taken out of an old, useless computer (which I will use for Xubuntu alone. I have other, larger drives which I will use for the data storage). I wiped it clean, and am in the install screen, and I'm struggling with figuring out how many new portions I need to make, how many Gigs to allocate to each one, and what format to give each. (/, /boot, /home, etc.)

I have an event I'm leaving for soon, so I'm not going to proceed any further unless I have a little more help. If someone can respond before 11:00 CST (Six and a half hours from the point of this posting) with this laid out, I'd greatly appreciate it.

Also, is there a certain format that I will need my extra hard drives to be in for them to work? Can I do that after I have the computer up and running?

---

### Post by darkod on 2011-11-27
1. You can do the data disks when ever you want.

2. The layout:
(X)ubuntu uses as minimum two partitions, called root and swap. The symbol for root is just / and that is the starting point of all the paths to all the files.
I always recommend creating a third one, /home, as separate partition because it helps with clean installs in the future. But for that you would need to use the manual partitioning option, because the auto options only create / + swap.

Sizing of partitions and filesystem:
/   ext4   as low as 5GB because linux programs are not space consuming (not too much)
swap   swap area   size 1.5 x RAM especially if you plan to hibernate. if not, it can be less but keep it at 2GB minimum for example. if you have plenty of RAM the swap might not be used a lot
/home   ext4   the rest of the disk

For a 20GB disk, I would say
/   8GB
swap   2GB or 1.5 x RAM
/home the rest

That should start you off.

---

### Post by bosler on 2011-11-27
> **darkod said:**
> 1. You can do the data disks when ever you want.

2. The layout:
(X)ubuntu uses as minimum two partitions, called root and swap. The symbol for root is just / and that is the starting point of all the paths to all the files.
I always recommend creating a third one, /home, as separate partition because it helps with clean installs in the future. But for that you would need to use the manual partitioning option, because the auto options only create / + swap.

Sizing of partitions and filesystem:
/   ext4   as low as 5GB because linux programs are not space consuming (not too much)
swap   swap area   size 1.5 x RAM especially if you plan to hibernate. if not, it can be less but keep it at 2GB minimum for example. if you have plenty of RAM the swap might not be used a lot
/home   ext4   the rest of the disk

For a 20GB disk, I would say
/   8GB
swap   2GB or 1.5 x RAM
/home the rest

That should start you off.

Well, I have 8 GB of RAM, so with 1.5x RAM, that'd take up the rest of the hard drive, so I'll probably do 4 GB, leaving me with 8 GB for /home.

Thanks for your response. I'll try that when I get home.

---

### Post by bosler on 2011-11-27
Okay, I don't see a swap. There's:
[LIST]
[*]/
[*]/boot
[*]/home
[*]/tmp
[*]/usr
[*]/var
[*]/srv
[*]/opt
[*]/usr/local
[/LIST]

Which one do I go with?

Never Mind. I see. Swap is a file system... Good to know.

---

