---
title: "Hoary doesn't use swap?"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by zee on 2005-04-24
Hi.
   A few days ago I installed Hoary on my laptop and designated a swap partition (1.5 Gig) in order to use hibernation but now it seems like the system is not using the swap partition at all.

   Output from free:
zidar@lili:~$ free
             total       used       free     shared    buffers     cached
Mem:        515924     414384     101540          0      23052     198800
-/+ buffers/cache:     192532     323392
Swap:            0          0          0
zidar@lili:~$

   I even added a fstab entry  for the said partition but to no avail. What to do/try next? A reinstall is not an option.

thans in advance,
zee

---

### Post by heimo on 2005-04-24
I've seen this. I don't know the reason why it happens, but it seems to be related to hibernation.

You can try to activate swap with [i]swapon -a
[/i]If it doesn't work, you can mkswap /dev/[swap_partition_here]
And then [i]swapon -a

[/i]This is just a workaround, the problem will come back. :-/

---

### Post by zee on 2005-04-24
I will try to really shut down the computer instead of hibernating it. Maybe this will alleviate the problem, though I do remember that one has to add a separate to Grub in order to wake the computer from hibernation.

thanks.
zee

---

