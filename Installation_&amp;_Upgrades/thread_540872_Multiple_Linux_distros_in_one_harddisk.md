---
title: "Multiple Linux distros in one harddisk"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by technomaniac on 2007-09-02
Hi everyone....I wud like to know how do i install more than one linux distro in one harddisk

---

### Post by forestpixie on 2007-09-02
read about dual/ triple boot - search here and Google and other distro sites

you just won't need to worry about reading ntfs 

depending on how many partitions you have you might need to uses extended partitions/logical partitions

---

### Post by [Alsharifi] on 2007-09-02
same way u would dual boot with Windoze..

you would only need one linux swap portion right?

---

### Post by forestpixie on 2007-09-02
> you would only need one linux swap portion right?

I believe that to be the case 

I think have more than one /home partition would cause problems though - sure I read that here

---

### Post by Herman on 2007-09-02
Yes, avoid making any installations with separate /home partitions, definitely. If you want to multi-boot you will want to install each OS in its own nice neat single self-contained partition, they can all share the same swap area too unless you use hibernation mode. Having too many partitions (separate partitions for each installation),  will give you a migraine headache.

You can only make four primary partitions per hard disk, or you can make one of them an extendable partition which can be then subdivided into quite a large number of logical partitions. Windows likes to be in a primary partitions but most Linux OSes can be in either type of partition, it makes no difference at all to most Linuxes. [Help on Partitioning]("http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning")

It doesn't matter if you install the boot loader for each installation to MBR or to the OSes first sector. Most other distros the use GRUB will be able to scan the hard disk for existing OSes and automatically add them to their /boot/grub/menu.lst for you or whatever they use as the equivalent.

If a new OS you are adding uses LiLo, you can still chainload it by the first sector from any GRUB loader providing you also install LiLo to the OS partition's first sector. Here's how, [ Run Liloconfig]("http://users.bigpond.net.au/hermanzone/p4.html#Run_Liloconfig").
            
If other OSes use GRUB, you can use GRUB's configfile command to boot them by their /boot/grub/menu.lst or equivalent.
[Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

Try to stick with good 'Parted based partition editors if you can, try not to mix and match partitioners if you can at all avoid it. [GParted -- LiveCD]("http://gparted.sourceforge.net/")
 is the best in my opinion. QTParted, Partman, Ubuntu's Gnome Partition Editor (based on GParted), are all good.

Have a [Super Grub Disk]("http://geocities.com/supergrubdisk/") ready in case of booting problems.

Consider making a dedicated GRUB partition first, and then installing all the  OSes boot loaders to the first sector of the OSes partition. Then add an entry to your main GRUB loader in your dedicated GRUB partition. 
[         How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

If you have more then one hard disk you can also chainload the MBR of each hard disk from GRUB in your first hard disk, then the OSes for each hard disk can be booted from their own GRUB menu, that means you don't need to have everything on the same GRUB menu in case it gets too cluttered. [chainloader boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader")  (Providing you install at least one OSes GRUB to MBR in the non-first disk).

If using GRUB seems too complicated for you or if it will be a lot of work, you can always use [GAG Boot Manager]("http://gag.sourceforge.net/"), GAG Boot Manager is quicker and easier to configure every time you add or remove an operating system. GAG is operating system independent and it's 'graphical', quick'n easy to use).  GAG needs each boot loader installed to its own partitions first sector because it works by chainloading only, but is very good for this type of use. (multi booting).

That's all I can think of right now, just have fun,
Regards, Herman :)

---

### Post by technomaniac on 2007-09-03
Thanks everyone.Thats all the info I need

---

