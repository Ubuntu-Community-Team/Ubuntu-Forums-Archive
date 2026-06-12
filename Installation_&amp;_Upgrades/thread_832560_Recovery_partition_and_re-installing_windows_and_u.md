---
title: "Recovery partition and re-installing windows and ubuntu"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by drjonze on 2008-06-17
Hi everyone,

When I installed Ubuntu (5 days ago, I'm the definition of a newbie) I saw that there was a small partition on my c drive. I was afraid to touch it until I later learned it was to re-install windows. I wanted to have 3 partitions for ubuntu, I wanted my /home directory to be its own partition. Because you can only have 4 on the hard drive and I'm dual booting, I could not do this.

I would like to get rid of that partition, re-size the partition that windows is on and re-install Ubuntu as I wanted to do it. How can I do this and still be able to re-install windows? Also, I've heard that I should install Windows first, but will it reformat the hard drive first and erase my partions before it re-installs?

Thanks!

---

### Post by wolfen69 on 2008-06-17
as far as i know, using the recovery partition will reformat the whole drive. you could then resize windows and create new partitions with [PartedMagic]("http://partedmagic.com/") (my fav)

btw, you can have more than 4 partitions by creating an extended partition and creating logical partitions within it.

---

### Post by logos34 on 2008-06-17
> **drjonze said:**
> I would like to get rid of that partition, re-size the partition that windows is on and re-install Ubuntu as I wanted to do it. How can I do this and still be able to re-install windows? Also, I've heard that I should install Windows first, but will it reformat the hard drive first and erase my partions before it re-installs?
 
I would recommend reinstalling ubuntu /, /swap amd /home on logical partitions inside an extended partition. Then the 4 primary partition limit is not an issue.  Leave the recovery partition, because if you delete it and grow windows to take up the empty space, it may screw up windows boot files/bootsector.  I wouldn't take a chance.

---

### Post by drjonze on 2008-06-17
Thanks for the tips. I knew there had to be other options. I know that I don't know enough to know what I don't know. :)

---

### Post by wolfen69 on 2008-06-18
everyone was a newbie at one time. i still consider myself a newbie, compared to some people. just enjoy it.

---

