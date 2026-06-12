---
title: "SWAP partition 16GB RAM needed or not ?"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by michal12 on 2015-07-29
Hi
I found good document about SWAP partition : [https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/s2-diskpartrecommend-ppc.html#id4394007](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/s2-diskpartrecommend-ppc.html#id4394007)

Do I need create SWAP partition ? This is standard PC with 16GB RAM - I use only 1 VM (with win..) and nothing special, and GNS3. I don't use hibernate. I asking because I have only 250 GB SSD drive.
If yes where do you recommend create SWAP partition on first or second partition ? 

System: ubuntu 14.04 LTS 64-bit 

Thanks for help.
M.

---

### Post by howefield on 2015-07-29
You'll probably find swap is so seldom used that you wonder why you have one, but it is probably best to maintain one for badly behaving applications, imo.

I have only 8GB of ram in this machine but have seen Libre Office and Virtualbox occasionally want to use swap even though there is plenty of real memory available. I keep swap on a mechanical disk separate from the SSD,  but if that is not possible for you I'd probably put a 4GB (ish) partition on the SSD and turn down swappiness.

---

### Post by michal12 on 2015-07-29
Thanks for info. 

If we speak about SWAP partition - where is recommendation to located SWAP partition ? 
I create 3 partition:
- /
- /home
- <swap>

SWAP is recommended to create on beginning or end of SSD disk ?
This is SSD disk probably this is don't matter. 

I create SWAP with recommendation 8GB. 

Maybe what is your recommendation to disk 250GB ?

Thanks for help. 
M.

---

### Post by howefield on 2015-07-29
> **michal12 said:**
> If we speak about SWAP partition - where is recommendation to located SWAP partition ?

I do not know if it matters on an SSD card where it is.

An interesting if a little old post/thread here you might be interested in..

[http://ubuntuforums.org/showthread.php?t=1937251&p=11746853&viewfull=1#post11746853](http://ubuntuforums.org/showthread.php?t=1937251&p=11746853&viewfull=1#post11746853)

---

### Post by oldfred on 2015-07-29
The argument on location on drive was about the difference in rotational speed of inner vs. outer tracks on hard drive. But SSD does not rotate. :)

But even the discussion of location on drive usually was not critical. And with the amount of RAM, you may never use swap. I agree with howefield's first post that having a little swap is often worthwhile, but not required.

I tend to make swap last on drive just to have it out of the way in case later I want to change partitions around. I use 2GB for new systems. My old system with 4GB of RAM never used swap, but I had 3GB of swap. I never hibernate, and do not do video editing which may be about the only application that would use swap or as much RAM as you can afford.

---

