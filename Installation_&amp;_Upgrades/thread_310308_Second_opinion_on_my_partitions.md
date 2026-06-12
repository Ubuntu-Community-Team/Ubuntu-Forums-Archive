---
title: "Second opinion on my partitions"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by danmbugua on 2006-12-01
[FONT="Trebuchet MS"]I partitioned my hard disk and installed Ubuntu Edgy Eft using the installation disk.

I have a 160GB hard disk. My partitions are as follows:
[LIST]
[*]/ 10GB Primary partition
[*]/tmp 10GB Extended partition
[*]/var 10GB Extended partition
[*]/usr 20GB Extended partition
[*]/usr/local 20GB Extended partition
[*]/home 75GB Extended partition
[*]/swap 4GB Extended partition
[/LIST]

My processor is AMD64 Athlon. My memory modules are 2GB.

Any second opinion? :-k [/FONT]

---

### Post by Tilex on 2006-12-01
I am by far an expert, hence this question: why are you partitioning your disk that way?  :-k

---

### Post by danmbugua on 2006-12-01
[FONT="Trebuchet MS"][LIST]
[*]/ 10GB Primary partition     - for Ubuntu. Might be the only OS I'll be using as a base. Am thinking of using Xen or VMWare for other distos, if need be.
[*]/tmp 10GB Extended partition  - thought of separating this from /. I'll be using graphics intensive games / dev tools
[*]/var 10GB Extended partition  - didn't have a concrete need for this. At most I'll be having two active users. This is a home desktop which I'll be doing developing/programming on. Mail might be the main beneficiary of this partition.
[*]/usr 20GB Extended partition  - I intend to install many Main and Restricted repository packages, i.e packages supported by Ubuntu. I figure they'll end up in this partition.
[*]/usr/local 20GB Extended partition  - Will be installing many more universe and multiverse repository packages, i.e not supported by ubuntu. This is their partition.
[*]/home 75GB Extended partition  - I'll have a collection of music, movies, pictures, videos, etc on this. 
[*]/swap 4GB Extended partition   - with my memory modules of 2GB, I used doubled this for swap. Which is better, having the swap as a primary or extended partition?
[/LIST]
I have one primary partition for /. The other partition is an extended one for the uses above.

This is my first Linux box, hence the need for a second opinion.[/FONT]

---

### Post by Tilex on 2006-12-01
Oh, I see.  But it seems like you're wasting lots of hard disk space for details...I mean, this is my opinion, but it were my 160 gig (which I wish I had!), I would keep at least 140 gigs for the '/' since you don't have many users and then I would dispatch the rest the way you did it, but less everywhere.  Of course you will install lots of programs from the repository but '/usr/local' is a subset of '/', no?  

If you give, let's say, 140 gig to '/', don't you think the 0.S. will take care of the rest as your needs grow?

---

### Post by kylevan on 2006-12-01
my personal opinion (on my 80GB drive) goes something like this:

swap = 1.5-2 times your physical RAM

/boot = 100MB or so
/ = 10GB or so... you would need to install a LOT of stuff to fill that up.  I have every program I will probably ever use installed right now, and I'm using up under 4GB for my entire / partition excluding /home.
/home = whatever's left.

the /boot partition isn't even all that necessary for your average workstation, IMO, unless you have a bunch of custom kernels that you have built and want to keep if you wipe the rest of your disk.  the /home partition is there for what I hope are obvious reasons.  as an idea, you might wish to devote a partition to /var, but IMO, it's not all that vital unless you're running a mail server or something, as the main hog of space in there for me is just apt's package cache.

here's the first thing that popped up on google when I searched "linux partitioning guide"

[http://www.hccfl.edu/pollock/AUnix1/Partitioning.htm](http://www.hccfl.edu/pollock/AUnix1/Partitioning.htm)

---

### Post by danmbugua on 2006-12-01
[FONT="Trebuchet MS"]I thought it's prudent to separate /usr (used for packages), /home (for documents, pics, music, etc) from /, with the reason that with constant upgrades on the OS, these partitions are not affected. What's your view on this?

I'd do away with the unnecessary partitions if I figure in the long term they are worthless[/FONT]

---

### Post by kylevan on 2006-12-01
well, often the applications contained in /usr are upgraded along with the changing distro.  if you have a lot of non apt stuff that you'll be using (like seperately downloaded Google programs, as an example) you might want to create the /usr/local partition.

I personally wouldn't do an in-place upgrade between versions of a distro. Besides, I pay the same amount for my DSL line whether it's used or not, so a good session with apt isn't arduous to me.

---

### Post by danmbugua on 2006-12-01
How much hard disk space should be assigned to /tmp and /var for a home office/desktop?

---

