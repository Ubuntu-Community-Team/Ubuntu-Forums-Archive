---
title: "Poor performance with Heron on an EeePC 900"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by three08 on 2008-10-08
As the title suggests, I'm having some performance issues with the install of Heron I have on my Asus EeePC 900. It has 1GB of RAM and a 900MHz processor, but it can't even run Firefox 3 without hanging regularly. (By hanging I mean that it stops responding.) Every application does this, too, so it's not just Firefox - Pidgin, the file manager, most everything. I've had to reinstall Ubuntu a couple of times, and this problem only happened since the most recent install.

Two days ago I booted up GPartEd to format my USB flash drive and I noticed the swap file was around 690MB. I know it's supposed to be 2x your amount of RAM - in this case 2 GB - so instead of formatting the flash drive, I booted from it, loaded GPartEd from the flash drive, shrunk the main partition, formatted the swap partition, and recreated it at the proper size. Since then the hanging has gotten worse and I have to wonder if my computer is failing to properly register the swap partition or something. The mount point may have changed, which adds to my concern. Initially, the 690MB swap partition was on a logical partition because my first install of Ubuntu was while dual-booting both Heron and the computer's native OS (which, I believe, is a custom build of Xandros).

Does any of this make any sense? Sorry. I had never even seen a Linux machine until I bought this computer.

EDIT
Now I feel dumb posting here to ask this. Google answered my question easily enough. If anyone else has the same problem, here is the page I used to solve it:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
It's easy enough to use the tools provided in that process to reattach your swap partition, if you have one. I did and performance seems to have improved.

---

### Post by greenwom on 2008-11-03
I have an eeePC and I've have hardy on it for a while.  With a recent reinstall I've also noticed really poor performance...

1.  I have 2 gigs of Ram with no swap.  In the past I've had no swap and there wasn't any of this gray-screen waiting and slow response.  

my $free with just a terminal, firefox, and thunderbird.
```
Mem:       2067184     993316    1073868          0      13668     520520
-/+ buffers/cache:     459128    1608056

```

Looking at the system monitor I see that Firefox is using 141mb at idle thunder bird and the gnome panels are at 20mb.  

So what's causing this slow down, I've never had a swap on the eeepc

---

