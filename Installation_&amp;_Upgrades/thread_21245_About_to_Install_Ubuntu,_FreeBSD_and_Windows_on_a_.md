---
title: "About to Install Ubuntu, FreeBSD and Windows on a dell..."
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by Francisco on 2005-03-21
I have been wondering, is this possible? I guess it is, since I have run double boot systems with windows before, but what about 3 OS's?

 What are your recommendations on what to install first? - Do I have to give each install their own partitions SWAP partitions and /?

Thanks.

---

### Post by armitage on 2005-03-21
well, as for triple booting, you can do that. heck, ive seen people with even more...

anyway, as for installing, windows has to go first. after that, you can pick and choose which goes next.

each OS has to have their own partition. as for swap, well if the other os was another distro of linux, you can share the swap partition with both linuxes, no problem there... but since your third os is freebsd, im not so sure. I guess you would have to make its own swap partition.

---

### Post by Juergen on 2005-03-21
For freeBSD you create a 'slice', which is like an 'extended partition' in other OS.
AFAIK you can't use existing 'extended' partitions for this, so don't use up all your (primary) partitions.

Maybe something like this would work (I've not tried to have 2 ext. partitions so far):
- Windows on a primary
- extended Partition with all Linux partitions in it
- BSD-slice with all freeBSD partitions in it

As for sharing swap, there's a mini HOWTO here:
[http://www.tldp.org/HOWTO/Linux+FreeBSD-3.html](http://www.tldp.org/HOWTO/Linux+FreeBSD-3.html)

---

