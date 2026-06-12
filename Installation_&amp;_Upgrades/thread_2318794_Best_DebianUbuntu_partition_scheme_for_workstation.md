---
title: "Best Debian/Ubuntu partition scheme for workstation"
date: 2016-03-29
forum: Installation &amp; Upgrades
---

### Post by jason-cordero on 2016-03-29
I have a workstation with 16 Gb RAM, one SSD 250 Gb and one HDD 1Tb. I  would like to install both Debian and Ubuntu, and I planned something  like:
  
[LIST]
[*]/SWAP --> 16 Gb in SSD 
[*]/ (Ubuntu) --> 118 Gb in SSD 
[*]/home (Ubuntu) --> 400-500 Gb in HDD 
[*]/ (Debian) --> 118 Gb in SSD 
[*]/home (Debian) --> 400-500 Gb in HDD 
[/LIST]
  so that I can share the homes across Ubuntu and Debian.
  Now the question is, should I move /tmp and/or /var and/or /usr to a  separate partition in the HDD? And how much space would you keep for  each one?  I could have more free space in the SSD in that case, but I  do not know which one of those I should put into another partition.  Could you also tell me what do you think about 16Gb SWAP? (I guess it is  enough, since I already have a lot of RAM).
  I would appreciate every comment.

---

### Post by Bucky Ball on 2016-03-29
*Thread moved to **Installations and Upgrades**.*

Why have two /home partitions and such a large /swap? You only need a /swap that big if you intend hibernating. Maybe you do. Two Gb is generally adequate, especially with that much RAM (some users don't use a /swap partition at all, I don't advise that). 

Install one OS. When installing the other, choose 'Something Else' at the partitioning section. Mark the /swap you created in the first install to 'Use' and the /home to 'Use' but not to format.

If you have a separate /home partition, regardless of how you do it, there is no point whatever in have a 100Gb+ / partition. Why? A Ubuntu install will fit easily on 25Gb (I've never used more than a 15Gb partition myself but run a pretty slimmed down hybrid) as all your personal data - Video, Documents, Music, etc. - goes in /home. The OS goes in root and after install will probably take up less than 10Gb.

Make the / partitions 20-25Gb if you have a separate /home. I would be seriously rethinking your current plan in light of the info in this post.

PS: Keep in mind we are a Ubuntu forum so we can give most effective support for Ubuntu. If you want help with Debian, best to post a new thread on the Debian forum. 

Good luck. ;)

---

### Post by QLee on 2016-03-29
I have been both a Debian and Ubuntu user for a long time and I can't think of a reason to use a different partitioning stratety for the two different operating system, especially since Ubuntu is based on Debian.

I think you should consider the advice previously given and I would offer a few more suggestions. I currently use 30 GiB Operating System partitions and haven't filled one with upgrades. It might be useful to go with smaller /home and use a separate "data" (or whatever you want to call it) partition which you could then mount in your /home or link folders from to your /homes. Personally I would not try to share one /home between Debian stable (or whichever version you choose to use) and Ubuntu. If you are going to use a 16GiB swap so that you can hibernate, then consider making a separate swap for each operating system so that they could be hibernated separately because if you hibernate one and boot the other with a single swap and it uses swap it could overwrite the other's hibernate info. Control which swap is which with the fstab of each OS.

You could consider another partition to test other flavours or versions of Linux and I personally would leave a little bit of unpartitioned space on the ssd.

Keep in mind that your SSD is likely faster than your HDD and that could become a factor to consider depending on how and what you use your computer for. 
  
There is a huge amount information available with a search engine that gives many different ways to partition based on the writers' personal preferences, you can find it easily and see what else applies to your specific situation because what is "best" is situation specific, based on how you use your computer and backup strategy.

One such is the Ubuntu "official" suggestions:
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by Bucky Ball on 2016-03-29
Good points above, some of which I overlooked. Something else I'll add. 

I have a number of installs on the laptop. I allow the /home directory to be created by default in / in each install, delete the default folders in the default /home, like Documents, Videos, Music, etc., and create symlinks to that contain that data in directories on one big data partition (/storage). That way, all installs use the same data, no redundancy, no confusion. If you change a personal file, say a text document, while booted into one install, those changes are reflected when you boot into another.

And yes, put the OSs on SSD, everything else on the HDD (and a lot of people include /swap in everything else).

---

