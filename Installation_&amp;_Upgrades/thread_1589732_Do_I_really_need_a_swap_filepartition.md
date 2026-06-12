---
title: "Do I really need a swap file/partition?"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by jkounis on 2010-10-06
On my first Ubuntu Installation, I had a 512MB of memory with a 512-MB swap partition.
Then I had 1 GB of memory with a 1-GB swap partition.
Then I had 4 GB of memory with a 4-GB swap partition.
Now I have 6 GB of memory with a 6-GB swapfile.

My new computer has 12 GB of RAM.

Since the amount of RAM that my new computer exceeds anything I have ever had before, do I really need a swap partition and/or swap file?

It seems to me that the only real reason you need a swap partition is if you may run out of memory, or to swap inactive processes out of memory so you have more RAM available for disk caching. Am I missing something?

---

### Post by psusi on 2010-10-06
Hibernation relies on swap, but yea, if you don't plan on ever actually using the majority of that ram, or hibernating, then no, you don't need swap.

---

### Post by efflandt on 2010-10-06
In case anyone tells you that you need swap to "suspend", you don't.  You only need swap = RAM to hibernate.

Even when running from a USB drive on an 8 GB PC I was able to suspend (which did stop the USB drive) and resume.  There is a 2 GB swapfile on the drive in case it is used with another computer, but it is not used at all for this one.

---

### Post by oldfred on 2010-10-06
I recently saw a post from Herman where he said some swap is still a good idea. He was not sure why, but assumed something about the kernel initially looking for swap. I did not save link.

I still suggest 2GB or RAM is you want to hibernate. With the sizes of hard drives now 2GB makes no difference.

---

### Post by NightwishFan on 2010-10-06
I would have a small swap 1g? Just in case you run out of memory due to a bug, swapping tends to nip it down to let you kill the process in time.

---

### Post by Johansen on 2010-10-07
I ran 10.04 on a laptop for a while with no swap, and i've run debian lenny on a desktop with no swap either. 
 
the only problem is when it runs out of ram, interesting things can happen. generally when a program runs out of ram and then runs out of swap ubuntu can figure it out so to speak and the system will still operate, either the program will halt or crash. not always the case with no swap, it may lock up the computer.
 
because there are still memory leaks in evolution, notify-osd, pidgin and various other programs, adobe flash plugin for firefox, java, etc you may find that just because you never use more than a gig of ram now, don't mean you won't use 2 gigs next week after another update.

---

