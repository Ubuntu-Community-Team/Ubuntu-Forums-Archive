---
title: "New install killed my ability to boot to an old install (multiboot)."
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by gnumd on 2008-05-02
I don't want to post in too many places.
I think this post should have been put here however.

[http://ubuntuforums.org/showthread.php?t=778800](http://ubuntuforums.org/showthread.php?t=778800)

I'm having a problem with a multi-boot system and need to fix my mbr to access a prior installation of Ubuntu 7.10 with a separate /home partition.

Can someone help me or direct me to some simple steps (or complicated ones that move slowly).

Thanks.  
~gnumd~

---

### Post by Pumalite on 2008-05-02
Be more specific.

---

### Post by gnumd on 2008-05-02
I had a working Ubuntu 7.10 running off an SDHC on my eeePC.  The /home partition was on the internal SSD, also a boot partition was on the internal SSD.  I didn't install Grub to my knowledge and it was working fine telling the eeePC to just boot off the SDHC.

I messed it up however when I tried to install GnewSense to an external USB HDD.  Now I can only get into the GnewSense even though my SDHC Ubuntu intall is still intact and undisturbed.

So I think the GnewSense did something to the boot partition that I had, and that partition must have been helping the SDHC Ubuntu install work properly.

So my question is HOW do I fix this situation?

Is it possible to use the Ubuntu LIVECD somehow to put ONLY a grub booter on the SDHC card without disturbing the /HOME partition on the SSD and previously installed files on the SDHC but still get them to find each other to work properly? 

I'd like to keep the working GnewSense on the HDD and still be able to get to it, but for most of my purposes I need to be able to run the prior installed Ubuntu 7.10 until I am smart enough to get internet and the right FREE/LIBRE software working under gnewsense.

Thanks.

~gnumd~

I apologize for cross-posting but I can't go without my files in Ubuntu much longer and don't want to just start into things on my own or try fixes that are for situations different than mine and mess things up in a way that can't be easily fixed.

---

