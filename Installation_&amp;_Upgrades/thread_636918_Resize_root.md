---
title: "Resize /root"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by Luci4 on 2007-12-10
I have the 64 bit gutsy, but my /root partition is getting too small....
This is what it looks like:
windows c: 15gb
my own d: 30gb
/root: 6gb
/home: 6gb
swap: 500mb
(and an external harddisk)

I can cut off from my D: drive, but I don't know how to give that size to /root.
I have partition magic, so I can free up the space easily, but don't know what to do next.
gparted apparently doesn't really work well with the 64-bit...
partition magic does recognise the linux partitions, but I don't know if it is able to actually resize them and whether that srews anything up or not (I'd rather not try before asking).
I also heard that swap should be double the size of your ram, so in my case that should be 1024. Is that also a reason why my ubuntu is rather slow (slower than my windows!)??

Hope you can help!

- Luci

---

### Post by psusi on 2007-12-10
Boot from the livecd and use gparted to resize the partitions, extending your root partition to be as large as you like.

---

### Post by logos34 on 2007-12-10
> **Luci4 said:**
> I can cut off from my D: drive, but I don't know how to give that size to /root.
I have partition magic, so I can free up the space easily, but don't know what to do next.
gparted apparently doesn't really work well with the 64-bit...
partition magic does recognise the linux partitions, but I don't know if it is able to actually resize them and whether that srews anything up or not (I'd rather not try before asking).
I also heard that swap should be double the size of your ram, so in my case that should be 1024. Is that also a reason why my ubuntu is rather slow (slower than my windows!)??

Hope you can help!

- Luci

running x64 here too. 

Haven't noticed any gparted problems with 64-bit.

Make sure you use the latest version of gparted live cd (0.3.4).  Note that shrinking D: down will take but just a sec, but expanding root to the LEFT into the free space will take quite a while (it has to copy/move all files to the front of the partition).

swap: 2x ram is the general rule, but I have yet to use more than ~400MB, so I just recently shrank my 1 gig swap down a few hundred megs to add to root.  

As for speed that's not the issue...or rather if it was it would be a case of the linux swappiness being to high (hdd thrashing is a sure sign of that).  But you're probably running the default setting, which IMO is best for average usage.  So something else is slowing ubuntu down--try turning off indexing or checking to see what processes are hogging your sys resources:

$ top

---

