---
title: "HDD Not recognised"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by tails29 on 2011-03-15
Hi,

I'm new to Ubuntu 10.10 and having problems when trying to install it. For some strange reason when it comes to 'Allocate drive space' my hdd isn't there. I first tried to install beside windows xp, then i took it off and tried it when the hdd was blank, but it still won't show my hdd.

Why won't it recognise my hdd?

any help is much appreciated

---

### Post by coffeecat on 2011-03-15
Hi and welcome to the forum.

Have you ever used your HD in a RAID array? Residual RAID metadata can cause just this problem. If you have, I'll search out the fix for you.

---

### Post by tails29 on 2011-03-15
It just a sata drive on it's it own i have, should be setup up as RAID, i'll double check tonight when i get home

---

### Post by coffeecat on 2011-03-15
If it's on its own now it won't be in a RAID array, but if it was once used in a RAID then some metadata can get left behind, and this confuses the installer.

When you get home, boot up the live CD and select "try Ubuntu" which will take you to the live desktop. Then open a terminal (Applications > Accessories) and post the output of this command:

```
sudo fdisk -lu
```

It won't tell us about possible RAID  but it will be useful information to have. In the meantime I'll ask someone else to have a look at this thread to see if there is anything else to suggest.

---

### Post by Grenage on 2011-03-15
> **coffeecat said:**
> It won't tell us about possible RAID  but it will be useful information to have. In the meantime I'll ask someone else to have a look at this thread to see if there is anything else to suggest.

Ahoy there,

Out of curiosity, wouldn't using dd to 'zero' the disc be a sure fix for the metadata?  If it's at the beginning of disk, a small segment could be done.

P.S: I love your avatar.

---

### Post by coffeecat on 2011-03-15
> **Grenage said:**
> Out of curiosity, wouldn't using dd to 'zero' the disc be a sure fix for  the metadata?  If it's at the beginning of disk, a small segment could  be done.


I'm sure you're right. For the record, the fix I was going to suggest is in this post:

[http://ubuntuforums.org/showpost.php?p=10559134&postcount=5](http://ubuntuforums.org/showpost.php?p=10559134&postcount=5)

But as I haven't any personal experience of running that, I thought it would be best to get the OP to confirm that the HD was used in RAID at one time. I've also asked Rubi1200 to have a look.

> **Grenage said:**
> Ahoy there,

A true Portsmouth greeting!

> **Grenage said:**
> P.S: I love your avatar.

Sorry, what did you say? The music's a bit loud. :wink:

---

### Post by Grenage on 2011-03-15
> **coffeecat said:**
> I'm sure you're right. For the record, the fix I was going to suggest is in this post:

[http://ubuntuforums.org/showpost.php?p=10559134&postcount=5](http://ubuntuforums.org/showpost.php?p=10559134&postcount=5)

Ah, good call; that's somewhat more precise, and I'll wager much quicker.


> **coffeecat said:**
> A true Portsmouth greeting!

I wonder if the nautical terms will ever die out?

> **coffeecat said:**
> Sorry, what did you say? The music's a bit loud. :wink:

Poor kitty. ;)

---

### Post by Rubi1200 on 2011-03-15
If you do not intend using the drive for RAID, the metadata needs to be removed. Formatting the drive will not remove it, so use the command in the link coffeecat provided.

Also, we need to see the fdisk output also asked for.

Thanks.

---

### Post by tails29 on 2011-03-15
maybe a silly question but, should i do the fdisk before or after i use the command in the link provided?

---

### Post by Rubi1200 on 2011-03-15
You can do both :)

The before and after might actually be useful too.

When you post the output back here, highlight the text and then click on the # icon on the toolbar to wrap the text with code tags (makes it easier to read).

---

### Post by tails29 on 2011-03-15
Here we go was hoping to this earlier.

Before fdisk:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb4f98d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS
```Performed removing RAID metadata

After fdisk:

```
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb4f98d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS
```

Hope all this is right, gonna try install now and see what happens.

---

### Post by tails29 on 2011-03-15
Got it installed now :), thanks guys, much appriciated

---

### Post by Rubi1200 on 2011-03-16
No problem, you are more than welcome :-)

Glad this worked out for you.

---

