---
title: "Partitioning scheme and questions."
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by jc3835 on 2005-07-13
I've been reading a lot about partitioning hard drives for linux installations.
I'm trying to figure out the best scheme for my computers, reading recommendations in Debian manuals and on forums, including this one.
I know that the most basic setup is putting everything onto one "/" partition, even SWAP, although that isn't recommended. Currently, I've been using 2 partitions: / and SWAP. This works, but it's definitely not the best.

Is a /boot partition useful at all? This is the only partition type I can't really find info on.

It's looking like I'm going to go this route for my desktop, which I use, but also have a couple other accounts on... unless I can get good reasons not to:
[INDENT]/swap   - 2GB
/           - 3GB
/var      - 2GB
/usr      - 2GB
/tmp     - 500MB
/home  - 40GB+ (whatever I have remaining most likely)[/INDENT]

Any of those seem like overkill? Not enough space? Seems that I could potentially waste a lot of space with the /usr and /var paritions, and that I should just lump those with the root(/).
I was also planning on using ReiserFS for all partions... any issues with that? I know people have favorites when it comes to ext3 vs. Reiser, but I haven't been able to see any major differences.
Should /home be a different filesystem type, so that Windows could read it if need be? Say a /music partition that would be used by Windows and Linux systems... should that be FAT?

Thanks for all help.

JC

---

### Post by varunus on 2005-07-14
2GB for swap seems like overkill, unless you have 2GB of RAM and intend to use suspend to disk.

2GB for /var also seems like overkill, as my /var after a long amount of usage still is only 150 MB.

You may want to add more to /usr, since most programs get installed there.  Actually, I'd recommend just using /home, /, and a swap partition.  A separate /usr could cause problems if the software you install gets too large.  If you want to do it the way you have listed, add more to /usr, and I'd get rid of /var and just make it part of the basic / partition.

If you want to do it the way you have below:

(whatever you choose for swap)
3 GB for /
4 GB for /usr, or get rid of it and add to /
1 GB for /var, or get rid of it and add to /
rest for /home

I'd recommend a 3 partition setup though.  Just my two cents.

---

### Post by matthew on 2005-07-14
I would echo varunus's advice. You might also find this thread I started interesting:

[http://www.ubuntuforums.org/showthread.php?t=48561](http://www.ubuntuforums.org/showthread.php?t=48561)

I think basically it is a matter of personal preference. I would echo the recommendation to have / and /home separate with a swap partition. Other than that, unless you have special needs I wouldn't worry about it.

---

### Post by MrCheese on 2005-07-14
My own scheme, on a 40Gb hdd, has been for a few years and upteen different distros as follows. the only time I ever had space issues was with a SuSE system with masses of extra packages compiled & installed in /opt. It's essential to have /home on it's own partition or disk as it's then safe from upgrading - blowing away your data on a system with just a / partition is so-o-o easy.....

/boot - 20Mb
/         - 800Mb
/var    - 800Mb
/opt    - 2Gb
/usr    - 4Gb
swap  - 800Mb (have 768Mb RAM)
/home - all the rest.

Just one big hint - never, ever, ever try to put /etc on it's own partition!!! Yup, tried it & wept at the result :-(

---

### Post by jc3835 on 2005-07-14
Thanks for the feedback guys.
matthew, i did see your thread as well.

is it at all beneficial to have a separate /boot partition?

i usually do 2GB /swap going by the rule of thumb of 2xRAM for /swap.

i have come to the conclusion that it is mostly personal preference also.

i think i'll do /, /swap, /home... seems to simplify everything for a normal desktop install.

Anyone have any feedback on my question of which filesystem type to use for music/movie directories that will be shared between linux and windows systems?

Thanks again.

JC

---

