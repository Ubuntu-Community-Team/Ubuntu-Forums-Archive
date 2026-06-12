---
title: "Partitioning problems with Ubuntu Netbook Remix"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by eeppeliteloop on 2011-01-14
Hi. I am desperate.

I have an Asus Eee 1005HA - nothing too fancy. I want to install the latest version of Ubuntu Netbook Remix. I also want to keep Windows XP as is.

I got myself into the install process and have two choices for partitioning: use entire disk or manual partitioning. I of course choose the manual thing.

Once there, I see all my partitions (four of them, Asus Eee users will know why). I have nothing on /sda2 and want to use it. When I resize it (to create additional partitions for swap and all the rest, as usual), I get 'unusable' space instead of free space. I just don't know how to create the other partitions. I cannot do anything. The only remaining option is "New partition table", but I doubt this is going to delete/corrupt my Windows files.

What the hell am I doing wrong? This is sad because it went so smooth and easily with my desktop PC and Ubuntu... it detected Windows XP and I just had to tell the installation how big I wanted Ubuntu and it shrank Windows accordingly.

Thanks a lot for your support, it's gonna be appreciated.

---

### Post by darkdragn on 2011-01-14
Well, you answered your own question. There are four partition, and i'm betting they are all primary partitions. You will have to delete one, then create an extended partition to make all of your regular partitions in. Such as /boot /home / swap and so on and so forth.

A partition table can only support four primary partitions, I'm sorry, I wish there was something I could do.

---

### Post by eeppeliteloop on 2011-01-14
Wow! Thanks a lot. I absolutely didn't see that Delete button and just didn't think about it. I deleted the /dev/sdb2 physical partition and made a few more logical ones. It seems to be working now.

Thank you again!

---

