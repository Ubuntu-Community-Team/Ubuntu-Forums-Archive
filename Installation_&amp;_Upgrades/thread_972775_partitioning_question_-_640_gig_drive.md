---
title: "partitioning question - 640 gig drive"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by graysky on 2008-11-06
Looking for some advice about partitioning a new 640 gig drive I bought.  It will be used exclusively for LINUX.

Hardware:  The machine is an X3360 with 4 gigs of physical  memory.  

What is a good size for the root and swap partitions?  I don't want to mess with shrinking/expanding partitions in the future (assuming you can even do this with ext3).  I was thinking 20 gigs would be good for the root partition, and that 4 gigs would be good for the swap.  The rest would be for /home.

What do you guys think?

---

### Post by Elfy on 2008-11-06
Assuming it's 64bit (or server I think) and it'll see all 8Gb of memory then yea - 20Gb for / will see you fine I should think.

I personally though would set up data partitions and only use /home for configs - but that's just the way I like it :)

---

### Post by tommcd on 2008-11-06
> **graysky said:**
>   I was thinking 20 gigs would be good for the root partition, and that 4 gigs would be good for the swap.  The rest would be for /home.

What do you guys think?

Since you have such a huge disk it really doesn't matter, but 10-12GB for the root partition is plenty. My Intrepid install on my laptop currently shows only 2.6GB being used for the root partition. Slackware on my desktop with all of KDE and XFCE is only about4.5GB. So 12GB for root is more than enough, even if you install a lot of software.
With 4GB of memory you will probably never even touch your swap partition. I almost never touch my swap, even on my desktop, and my desktop only has 1.5GB of memory. A 1GB swap partition is more than enough for swap.
I also use a /data partition for my stuff. With that huge hard drive you could make several 10-12GB partitions, and use them to install several distros. They can all share the same 1GB swap; and they will all be able to write to the /data partition. The config files for each distro will live on the /home directory inside each distro's root partition. This way each distro's config files don't get mixed up, which could cause conflicts. And you can use the same user name for each distro.

---

