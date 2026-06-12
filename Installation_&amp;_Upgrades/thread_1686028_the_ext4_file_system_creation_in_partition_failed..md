---
title: "the ext4 file system creation in partition failed."
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by nazukeru on 2011-02-11
Hi, I'm admittedly a bit of a Linux n00b. I have had an experienced friend helping me but he too is at a loss. Doesn't help that he's a town over and we're trying to figure it out via Facebook chat. Whatever. 

This question has been asked before, I've read the threads, dunno if it's actually been solved. I'm ridonkulously sick right now so I can't really be bothered to search too much more than I have, and my husband needs this damn thing for work so here we go. This might get a little long winded. 

I have a Dell Mini 9 netbook. The SSD took a dump, so I ordered a Super Talent 16gb replacement. I put it in yesterday, tried to install 10.10 and constantly get errors. The first error, which I haven't had since, was [ERROR 30] Read-only File System. The install obviously failed. Wondering if perhaps the file got messed up in translation, I redownloaded 10.10, reformatted the flash drive (sandisk cruizer 4gb), put 10.10 back on via the program on the Ubuntu site. No luck, but no longer the [error 30]. Tried again using Unetbootin, no luck. Rinse repeat a few times, no errors just a working cursor spinning and spinning and spinning and spinning and.. you get it.

Tried to put WinXP on it just because I was that frustrated, no luck.

Now I'm back to Ubuntu (because let's face it, who wants to deal with Windows, christ they make it so complicated). I'm currently using 10.04 because I was hoping (praying) it might just be a 10.10 thing.

No such luck, now it goes to step 7/7, starts, and 5% of the way thry "creating ext4 file system" it  says "the ext4 file system creation in partition #1 (0,0,0)(sda) failed."  I have checked the SSD in the Disk Utility, SMART tests are clean. I have gone to terminal and run fdisk and had a smarter person than me look at the copypasta, no errors, I have deleted all existing partitions in gparted and started fresh. I have tried the auto partitioning, I have tried manual, I am going** insane**. Literally insane. My preschooler thinks I've leaped off the deep end.

Could it be my flash drive? Could the SSD be defective despite the tests coming back clean? What information do you need to help diagnose this? What do I need to type into terminal? Is there a way to entirely entirely entirely wipe the SSD to make it fresh-out-the-box clean? I will happily provide whatever you need if it means I can get my husband off my back about this stupid netbook with its stupid tiny keyboard.

Gonna go hold a pillow over my mouth and scream now, ta-ta~ thanks in advance for your help.

---

### Post by oldfred on 2011-02-12
Have you tried creating the partitions in advance with gparted? I always do that and then use manual install, but just have to choose partitions & formats. Install also goes faster if swap is created beforehand.

---

