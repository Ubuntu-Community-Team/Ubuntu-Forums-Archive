---
title: "Install WITHOUT reformat??"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by csb on 2006-11-08
I'm switching from another distro and want to install ubuntu in the partition where my previous system was located.  The partition is cleaned up and formatted for ext3 already.  There are about 35gb of files on the parition that I need to keep, so I'm not able to reformat the partition.

I'm telling the installer that I want to mount that big partition as /  .... but the installer is complaining that it needs to reformat it.  There must be some way around this... is there??  (clean partition, ext3 formatted)

Thanks

--csb

---

### Post by csb on 2006-11-09
bump

---

### Post by bulldog on 2006-11-09
The partition you want to keep you have to mount as /home otherwise it must be formatted.

You have to make a partition for / and for swap next to your /home.

---

### Post by csb on 2006-11-09
I understand that ... this partition *is* the partition I want to mount as the root partition, I just don't want it to be reformatted.  If I were to designate this partition as /home, I have no other unused space available for the root partition (so really, it's a problem)

So, the ubuntu installer FORCES a reformat of the root partition??  I think there should be some way around this, because I can imagine  a few scenarios in which someone wouldn't want to reformat.

If there's no way around it, then I have to go buy a new HD.  That makes Ubuntu expensive already, and I haven't even installed it yet.  ](*,)

---

### Post by bsussman on 2006-11-09
> **bulldog said:**
> The partition you want to keep you have to mount as /home otherwise it must be formatted.

1/2 correct - / must be reformatted.  However you can mount preexisting filesystems wherever you want.
> 
You have to make a partition for / and for swap next to your /home.Swap can be anywhere you like, including a different disk.

I am afraid your only easy choice is to shrink and mount your pre-existing data elsewhere.  Depending on what is in it, choose an appropriate mount point.

A related point - a separate /home is often a good idea.

---

