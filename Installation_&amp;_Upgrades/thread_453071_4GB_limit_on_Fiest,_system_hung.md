---
title: "4GB limit on Fiest, system hung"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by burnsje on 2007-05-24
** Installed Feisty with 2GB memory, system running fine **
When adding 2 more GB (total 4GB) system will not start, never receives login prompt.
System starts up, I see Ubuntu logo, then progress-bar completes, then black screen, but never see login.
System hangs.
Can  anyone help?

---

### Post by tgm4883 on 2007-05-24
hmm, 32 bit or 64?

---

### Post by burnsje on 2007-05-24
64 bit
Asus Striker Extreme board

---

### Post by tgm4883 on 2007-05-24
Try just changing the old memory for the new memory to see if the memory is faulty

---

### Post by burnsje on 2007-05-24
I have installed three different manufactures memory, all with the same problem.
I ran Memtest on current memory, no problems found.  I can boot any configuration or arrangement of 1GB, 2GB, 3GB but 4GB does not work.

---

### Post by Selage on 2007-05-24
The thing is that 4Gb ram is not that common and that the kernel is not configured for that.

Run 2 to 3 GB Ram and read a topic about recompiling the kernel.

This one is suppose to be a good one:
(didn't get there myself)
[Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=compiling+the+kernel")

Not that hard to do, you just need an Hour or 2 :)

Good Luck

---

### Post by shad0w_walker on 2007-05-24
The 64bit standard kernel is configured for 4Gb (I have it in this system)

Im not sure whats causing your problems but id suggest hoping over theo x86_64 support area. There are plenty of people over there that might be able to help you out.

---

### Post by hoggbottom59 on 2007-06-03
Why don't you try reinstalling and allow Ubuntu to repartition your root and swap partitions?

If you've upgraded your memory and there's still only the swap partition for less than 4Gb then it can't swap to the hard drive.

Just a thought, haven't tried it myself but have 1 Gb at present and thinking of upgrading to 2Gb.
The swap partition needs to be the same size as your memory doesn't it?

Leon.

---

### Post by tgm4883 on 2007-06-03
> **hoggbottom59 said:**
> Why don't you try reinstalling and allow Ubuntu to repartition your root and swap partitions?

If you've upgraded your memory and there's still only the swap partition for less than 4Gb then it can't swap to the hard drive.

Just a thought, haven't tried it myself but have 1 Gb at present and thinking of upgrading to 2Gb.
The swap partition needs to be the same size as your memory doesn't it?

Leon.

Thats not how anything works

---

