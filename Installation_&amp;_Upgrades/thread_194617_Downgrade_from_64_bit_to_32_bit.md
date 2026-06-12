---
title: "Downgrade from 64 bit to 32 bit"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by hauger on 2006-06-11
Hi.

I'm looking for some insight on how to go about downgrading from Kubuntu 6.06 x86-64 to Kubuntu 6.06 i386.  The reasons for this are owing to my not having +4GB of Ram and the hassle of working around problems to get 32 bit binaries running in the absence of 64 bit binaries (not to mention attempting to compile 32 bit source in a 64 bit world).

Anyways, I've downloaded and burnt a copy of i386 to a CD, thinking it would be as easy as putting it in, and telling the installer to install over the existing Kubuntu partition.  No good.  When I got to that point, it gave me three options:

1. Re-size the windows partition again, thus making 2 seperate Kubuntu setups and further limiting XP space.
2. Get rid of XP entirely and take over the entire disk.
3. Manually do everything myself.

Now, I'm not exactly an expert at manually editing partition tables, and by "not an expert" I mean "very likely to screw it up"

I know I could simply fix the MBR, delete the current Kubuntu partitions, resize the Windows XP partition back to 100%, and then do a fresh install again allowing Kubuntu's installer to create it's own partition, but what a pain in the butt.  Is there an easier way to go about this?

Thanks for any help.
Rob.

---

### Post by ironfistchamp on 2006-06-11
Erm now I am no expert but when getting to the partition bit you could manually go to the partition that it is currently on, say use this as root and format. It was pretty simple when I tried it. I did pretty much the same as you are trying. sure I lost everything but it was much easier in the long run.

I hope I have made sense.

Ironfistchamp

---

