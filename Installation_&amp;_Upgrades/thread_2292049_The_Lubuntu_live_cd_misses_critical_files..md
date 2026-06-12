---
title: "The Lubuntu live cd misses critical files."
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by Patser on 2015-08-24
While installing Lubuntu and getting to the disk partitioning settings i thaught to myself lets try something different today. b
So I setup my root fs with btrfs and also create a retarted large efi partition (which is required on almost all distro's
now-a-days). But after having that done and clicking to begin the install I got an error, so I went looking and found that the
btrfs tools are not even included into the live cd by default. This is a typical mistake because linux beginners whom have
no knowledge now cannot use this options sinds they do not know how to solve this problem.
Luckely I have been using linux sinds the dawn of mankind :P So I can provide the answer here for those who are reading
this an interested in trying btrfs:
Go to the console with ctrl+alt+f2 and enter apt-get install btrfs-tools.

Do do hope this is solved in the future for our beginners though...

Cheers.

---

### Post by sudodus on 2015-08-25
Welcome to the Ubuntu Forums :-)

The developers seldom read what is written at our Ubuntu Forums. If you want to get the attention of the developers you need to do it via some IRC channel or a mail forum. For Lubuntu, you can start via these links

[https://wiki.ubuntu.com/Lubuntu/GettingInvolved](https://wiki.ubuntu.com/Lubuntu/GettingInvolved)
[https://wiki.ubuntu.com/Lubuntu/Developers](https://wiki.ubuntu.com/Lubuntu/Developers)

---

