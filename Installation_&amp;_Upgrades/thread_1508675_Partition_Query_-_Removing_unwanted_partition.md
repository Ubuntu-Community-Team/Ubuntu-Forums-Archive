---
title: "Partition Query - Removing unwanted partition?"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by crispya on 2010-06-13
Hi

I'm not very experienced with Ubuntu. I upgraded to 10.04 via Update Manager (maybe shouldn't have done that . . . ) and had some problems, so tried installing 9.10 from the disc. It installed okay but created another partition - so now presumably I have 3 - Ubuntu 9.10, Ubuntu 10.04 and Windows XP.

I would like to remove the reinstalled 9.10 if possible and go back to using 10.04. The default OS is 9.10 and when I look at the Boot Options on start up, there's a few Ubuntu options beneath it (2.6.31-2 and 2.6.32-2) and I'm not sure which one is which.

So my question is, would it be wise to go back to using 10.04 and remove 9.10? And if so, how to go about that? Any help would be appreciated as I'm quite new to this.

---

### Post by darkod on 2010-06-13
Linux never installs in existing partition unless you use Manual Partitioning and tell it specifically which partitions to use. If you use the guided methods it will just create new installation as you noticed.

Deleting the 9.10 partitions is not a problem, but probably grub2 on the MBR is from 9.10 so you won't be able to boot anything if you just delete the partition.

If you select 10.04 from the grub menu, can you boot it? Does it work correctly?

Because you said you had some problems with it after the upgrade but didn't mention what type, can you boot it at all.

---

### Post by crispya on 2010-06-13
Hi there

So far 10.04 seems to be working correctly, although I haven't tried to do much with it. The problem was that I thought it had mucked up my wireless connection - turns out that was the router and not Lucid Lynx. In a panic, I reinstalled 9.10, hoping to undo any problems caused by upgrading. 

I've been having a bit of trouble working out what's what on the Grub menu - there are several Ubuntu options which is getting a bit confusing. I managed to navigate to 10.04 (by chance, I think!) and boot up with that and all my emails and settings are in that OS. Having another partition with 9.10 on it just seems a bit messy and unnecessary, but I don';t want to cause problems  by fiddling - if that makes sense.

---

### Post by darkod on 2010-06-13
The 32 kernel is from 10.04. In the menu the latest kernel for 10.04 should say like 2.6.32-21 or 2.6.32-22.

If you want to have 10.04 grub2 on the MBR you need to boot into 10.04 once, and if you have a single hdd just do in terminal:

sudo grub-install /dev/sda

That will put grub2 from the currently booted system (10.04) on the MBR of disk /dev/sda.

After that you might consider deleting the 9.10 partition so it doesn't create confusion. Unfortunately there is no "easy" way to integrate that space back into 10.04, there is slight risk if you want to add it. Maybe later if you decide to reinstall 10.04 as a whole, you can sort out the partitioning layout.

For more detailed information what you have where, you can run the boot info script from the link in my signature, from any booted ubuntu. You don't have to post it here, just look around, it has very good detailed info. Instructions for running it are here, it works both from live mode and a booted hdd installation:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by crispya on 2010-06-13
~Thank you - I'll look into this over the next couple of days - I really appreciate the help.

---

