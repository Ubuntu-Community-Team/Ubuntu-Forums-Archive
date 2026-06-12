---
title: "Installation Question"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by opivy1218 on 2008-07-16
I'm again thinking about installing Ubuntu, just because my hate for Windows. I recently downloaded a lot of stuff I really don't wish to re-download. So, my question is, if I install Ubuntu, will I lose all my movies/music on my hard drive? Or will they still be there?

---

### Post by Sef on 2008-07-16
1) **Back up** your files no matter what you do.  There are no 100% guarantees that all will go without incident.

2) You can keep them:

a) [Dual Boot]("http://www.psychocats.net/ubuntu/"), if they are on the Windows OS.

b) If they are on a separate partition, just don't delete that partition.

---

### Post by Pumalite on 2008-07-16
Before installing a new OS; as a matter of good practice one should backup EVERYTHING first.

---

### Post by snowpine on 2008-07-16
> **opivy1218 said:**
> I'm again thinking about installing Ubuntu, just because my hate for Windows. I recently downloaded a lot of stuff I really don't wish to re-download. So, my question is, if I install Ubuntu, will I lose all my movies/music on my hard drive? Or will they still be there?

Hi Opivy, welcome to the forums! The short answer is that it depends on what type of installation you do. Specifically, when you get to the Partitioner stage of the installation.

One option is "guided install--entire disk". This will wipe out everything on your hard disk, including Windows, music, movies, everything. 

The other option is called a "dual boot" and is accomplished in the partitioner by choosing "resize ____ and use the freed space." (For best results, you should defragment your windows partition first.) This will set it up so that Windows and Ubuntu coexist on your hard drive, and you can choose which one to use when you boot. You will be able to read the files on your Windows partition from Ubuntu (but not the other way around unless you specifically set it up). I definitely recommend setting up a dual boot while you are learning, that way you can fall back on Windows if necessary.

It's also worth mentioning that you can burn an Ubuntu Live CD. That way you can experiment with Ubuntu without making any changes to your hard drive. Make sure that it works on your computer and that you like it before you actually install. Just remember, it will be a little slow running of the Live CD, that's normal.

And I will close by mentioning that you should back up all your important files before doing any installation or partitioning, just in case!

edit: ps my experience is with Windows XP; if you are using Vista, don't listen to my advice. :)

---

### Post by Rallg on 2008-07-16
You will lose your files if you install Ubuntu incorrectly, given your setup. You will retain them if you install Ubuntu correctly, given your setup.

Best strategy would be to burn your files to CDs or DVDs, so you can get them later. But if you cannot o that for one reason or another, try this:

First, create a partition into which you will put your files. If your Windows is Vista, then you can use Vista's own Administrative tools to shrink your existing Windows partition, and create a new partition in the freed space. Note that if you haven't defragmented your drive lately, the partitioner may refuse to shrink your Windows partition by much.

If you don't have Vista, you can shrink Windows and create a new partition using the GParted partition manager, from the Ubuntu live CD.

In either case, consider using FAT32 as the format for the new partition. The advantage to FAT32 is that it can be read either by Windows or Ubuntu.

Second, move your files to the new partition. Later, if you remove Windows, you will not be removing your new partition. Also, if you ever need to re-install Ubuntu (or make a major change), it is helpful to have your important files on a "neutral" partition that exists outside the Ubuntu file structure. This is better than putting the files into a linux home partition.

Third, use GParted on the Ubuntu live CD to manually create partitions into which you will place Ubuntu. You will, at minimum, need an ext3 partition for the root (main file structure), and a linux-swap partition.

Finally, make sure that when you install Ubuntu, you use the manual install process, and carefully select the partitions for installation. This is the point where an error can hurt you! Be sure that you don't select the partition where you put your files.

---

### Post by Pumalite on 2008-07-16
If you use Vista; you have to allocate space for Ubuntu with the Vista partitioner first. You cannot partition with the Ubuntu CD
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

