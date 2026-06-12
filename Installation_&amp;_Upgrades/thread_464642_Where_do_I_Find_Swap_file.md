---
title: "Where do I Find Swap file"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by poppers1957 on 2007-06-04
OKAY, I screwed up.  I was installing Dreamlinux onto a hard drive that contained my Ubuntu OS 7.04.  I made a partition of 22 GB formatted reserfs.  I made a swap file partition of either 1.6 GB or 1.3 GB.  The screw up is, I do not remember which swap file is my Ubuntu swap.  I did not write down the amount of the new swap file I created for Dreamlinux.  How do I find out which one is which.  Is there a way to view my swap file in Ubuntu?  I have gone through the forums, and have tried gparted.  Gparted cd will not tell me if there is anything on the swaps at all.  :(

---

### Post by taurus on 2007-06-04
I assume you know that you can share the same swap partition for all your Linux distros.  No need to make a separate swap partition for each Linux distro.  

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by poppers1957 on 2007-06-04
Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        6380    51247318+  83  Linux
/dev/hdc2            9523        9733     1694857+   f  W95 Ext'd (LBA)
/dev/hdc3            6381        9352    23872590   83  Linux
/dev/hdc4            9353        9522     1365525   82  Linux swap / Solaris
/dev/hdc5            9523        9733     1694826   82  Linux swap / Solaris

I do know that I can use the same swap.   As a matter of fact , I wondered if making a different one would screw things up.  On the Dreamlinux site, it was suggested that I do.  However I just may go back to the one.  But I still don't know which one to undo.  Does this output help you to help me tell which one is which?  Thank you for your help.

---

### Post by ryanVickers on 2007-06-04
As for this:
> Gparted cd will not tell me if there is anything on the swaps at all.
There isn't really anyhting in them ever as far as "files", just stuff that would be in ram if there was the room for it.

But to find the one it's using, maybe look in /etc/fstab to see which one it's mounting (using), but make sure you know the device names (check gparted, it'll tell you) or this won't be any use!

---

### Post by Ptero-4 on 2007-06-04
MY advice, dump the one at hdc4, it`s the smaller of the two and is the one next to the linux partition (delete the swap and your linux partition can be resized over w/o deleting/moving anything else).

---

