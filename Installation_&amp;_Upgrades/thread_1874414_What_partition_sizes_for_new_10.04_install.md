---
title: "What partition sizes for new 10.04 install?"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by Jiawen on 2011-11-03
In the next few days, I plan to install 10.04 on a new computer. It will have a 1 TB hard disk, but a big chunk of that will be Windows 7. I'm wondering what sizes of partitions I should use.
[LIST=1][*]The new build has 8 GB of memory, so I assume that means I should use 64-bit 10.04. Will file sizes be affected by using 64-bit? (Does / need to be a different size, specifically?) Is 64-bit even a good idea?
[*]I'd like a big chunk of that 1 TB to be accessible to both OSes. Is FAT32 still the standard for that purpose?
[*]Is the "double RAM" rule for swap still true? In other words, should I use 16 GB of swap?[/LIST]Thanks!

---

### Post by Script Warlock on 2011-11-03
1.no
2. use ntfs if you want both can access
3. true

---

### Post by papibe on 2011-11-03
> **Jiawen said:**
> 
The new build has 8 GB of memory, so I assume that means I should use 64-bit 10.04.
Using the 64bit version would be a good idea (however because of PAE extension the 32bit can work also, read more about it [here]("https://help.ubuntu.com/community/32bit_and_64bit")).

> **Jiawen said:**
> 
I'd like a big chunk of that 1 TB to be accessible to both OSes. Is FAT32 still the standard for that purpose?
No. NTFS would be much better.

> **Jiawen said:**
> 
Is the "double RAM" rule for swap still true? In other words, should I use 16 GB of swap?
Not really. With that amount of RAM, you could get away without any swap space. There are two consideration to set the size of the swap area:
[LIST=1]
[*]If you want hibernation, you need to at least  match your RAM.
[*]In case you are running 'super intensive' RAM applications swap can help you there (for example several Virtual Machines running all at once)
[/LIST]
Hope it helps,
Regards.

---

### Post by Jiawen on 2011-11-05
Thanks, both of you! That's very helpful.

---

### Post by dFlyer on 2011-11-05
My advice would to have at least a 20 gig / (root) folder, 16 gig swap and give yourself a separate /home folder as large as you can spare at least 100 gig or more, the home folder is where you save all your files in. You may also want a separate NTFS partition if you want to share files between windows and linux.

---

### Post by bluexrider on 2011-11-05
Use NTFS
32 bit for 4GB or Less
64 bit for 4GB or more
Windows needs to be happy on the so it should be on the first hard drive, first partition and the first sector. Rule of 3
You don't need a swap with that much memory however putting a swap at the end wouldn't hurt.

---

### Post by Jiawen on 2011-11-12
> **dFlyer said:**
> My advice would to have at least a 20 gig / (root) folder, 16 gig swap and give yourself a separate /home folder as large as you can spare at least 100 gig or more, the home folder is where you save all your files in. You may also want a separate NTFS partition if you want to share files between windows and linux.Sounds like you agree with the "double RAM" rule? Can you explain? (Not that I doubt it, just that I'd like to understand more.) 

I was planning on / of about 40 GB and /home of about 250 GB. :) 
> **bluexrider said:**
> Windows needs to be happy on the so it should be on the first hard drive, first partition and the first sector. Rule of 3I was planning on installing Windows first, shrinking the install from within Windows, then installing Xubuntu later. I assume Windows installs itself in the right place...?

---

