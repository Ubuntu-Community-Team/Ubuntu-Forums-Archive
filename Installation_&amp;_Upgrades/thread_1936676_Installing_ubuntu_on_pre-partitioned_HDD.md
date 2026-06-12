---
title: "Installing ubuntu on pre-partitioned HDD"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by Paapaa on 2012-03-06
I used Gentoo for years. Then went back to Win7 and now need Linux again. I think Ubuntu-64bit is the way to go now. I have my Gentoo HDD partitioned like this:

1. Small /boot partition. (Don't remember the size, ext2)
2. 512MB Swap partition.
3. 60GB / partition, ext4.
4. 100GB /home partition, ext4 with data to be saved.

Questions:

1. Can I install Ubuntu and utilize all the above four partitions?
2. Can I install so that /home partition is left intact?
3. Let's say there is a /home/Paapaa directory for the user Paapaa. If I create user "Paapaa" in Ubuntu, is it OK if the directory is already there with data in it? Or should I rename the directory first and copy all I need later to the new ~/Paapaa?

4. Should I use the default installer to accomplish all the above?

---

### Post by Paddy Landau on 2012-03-07
> **Paapaa said:**
>  1. Can I install Ubuntu and utilize all the above four partitions?
You don't need a /boot partition, although you may have one if you choose. It is really unnecessary, though.

> **Paapaa said:**
> 2. Can I install so that /home partition is left intact?
Yes. When you install, do *not* use the default. Instead choose to manually partition. Just choose each partition for its use, and tick "format" for all *except* the /home partition.

But, as with any installation, there is always a (small) chance of data loss, so please back up first!

> **Paapaa said:**
>  3. Let's say there is a /home/Paapaa directory for the user Paapaa. If I create user "Paapaa" in Ubuntu, is it OK if the directory is already there with data in it?
Yes, that is OK.

But, as already stated, there is always a (small) chance of data loss, so please back up first!

> **Paapaa said:**
> 4. Should I use the default installer to accomplish all the above?
As already stated, no; choose manual partitioning.

By the way, your swap should be equal to your RAM (or greater), but at least 1Gb. If you have a 2Gb or more, you can use 64-bit without problem; 1Gb or more, 32-bit; less than 1Gb, rather choose [Lubuntu]("https://wiki.ubuntu.com/Lubuntu").

---

