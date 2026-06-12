---
title: "Dual boot on existing XP box"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by sbergman27 on 2006-09-21
Hi guys,

I have a friend who is wanting to dual boot his existing Windows XP box with Dapper.  The drive is completely Windows.

He asked about partition magic, and I realized that as someone who switched entirely to Linux in 1997 and has never looked back, I'm the worst person in the world to ask about the options.

He could do a new hard drive.  Not sure if cost would be a problem.  

He could do partition magic, which I believe is payware, but the freely downloadable version might be adequate.

Then there is the gparted live CD.  

And then there is the possibility of just repartitioning during the install.

Can the dapper installer shrink an ntfs partition?

I have no Windows machine to test on.

Anyway, before I give any advice, I figured I'd better consult with people who are likely to have more recent experience with this kind of thing.

Thanks,
Steve Bergman

---

### Post by meng on 2006-09-21
I simply got the Ubuntu text installer to shrink the NTFS partition to create space. Neither the graphic nor the text installer can handle all situations, and perhaps they have problems with especially large drives, based on some of the posts to these forums. However, the installer worked perfectly in my case, and for many other users as well.

Some others try using PM or GParted LiveCD to partition before the install, but in my opinion this is not necessary and is unlikely to prevent problems from occurring during the install itself.

---

