---
title: "all drives gone #madWindows7user"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by samarpantthulung on 2013-01-12
I used an old version of PTD (partition table doctor):mad: and right after opening it, I closed it and later restarted. But the windows said it couldn't start, so, i used the bootable CD of windows 7 to repair and now, i don\'t find any of my drives :O can anyone help me?? is this normal?

---

### Post by dino99 on 2013-01-12
i hope you have tweated your partition(s) when they was unmounted; otherwise big troubles can happen, included data loss.

you might use genuine tools, not exotic non trusted ones.

and now:

boot in rescue mode

---

### Post by darkod on 2013-01-12
First of all, you need to specify whether you had a dual boot, and which version of ubuntu you have/had.

Otherwise, PTD sounds like windows program. If you were using a windows program, did win7 repair, and win7 can't boot, why would you be posting that in ubuntu forum? I didn't see even one reference to ubuntu in your post.

Use your ubuntu cd to load into live mode (Try Ubuntu option), open terminal and post the output of:
sudo parted -l (small L)

Also, you might install boot-repair into the live mode session, run it to create the bootinfo, and post the link it gives you. That will show us more details.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dorruk on 2013-01-12
The exact same problem happened to me once.

The drives were as well not visible in my case. Because partition tables were gone.

You could just rewrite partition tables using testdisk from terminal. I hope it's the same case, because I fortunately did not lose any data. :)

---

### Post by Mark Phelps on 2013-01-12
> **samarpantthulung said:**
> I used an old version of PTD (partition table doctor)
You knowingly used an (at-least) 4-year old program -- when new ones are available for free??  

You should have FIRST, gone to a Win7 forum (sevenforums.com is a good one) and asked there  They would have told you that you can get a CURRENT version of Minitool Partition Wizard for FREE -- and could have used that.

If you really want to get Win7 and your partitions back, then go to the Win7 forums -- these are the Ubuntu forums.

---

