---
title: "Partition fun"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by uncleclinto on 2007-09-22
Hey kids,

I've been reading about partitioning in the following documents ([https://help.ubuntu.com/7.04/installation-guide/i386/module-details.html#partman](https://help.ubuntu.com/7.04/installation-guide/i386/module-details.html#partman), [https://help.ubuntu.com/7.04/installation-guide/i386/partitioning.html](https://help.ubuntu.com/7.04/installation-guide/i386/partitioning.html)), but I'm still not sure how to do what I need to do.  

I have a Dell 4100 with a slightly damaged hard drive.  I'd like to set it up with Ubuntu for my wife to use as a surfer and emailer.  My problems are, of course in the first 4,000 blocks of my 20gb hd.  I want to partition my drive so that ubuntu installs in the second 9.8 GB of my hd to avoid problems altogether.  I really don't know that much about how all of this crap works so I may sound like an idiot already.  I just want to know how to tell Ubuntu to ignore the first 9.4 GB of my HD and install in the second 9.8, while keeping about 800 mb for swap at the very end.  

Any help would be greatly appreciated.  Meanwhile, I'll just play around because I can't really hurt anything.  This is essentially a big paperweight anyway.

---

### Post by logos34 on 2007-09-22
You might want to run a S.M.A.R.T diagnostic on the drive first--there's a slight possibility it's failing.  From the ubuntu live cd:

**sudo apt-get install smartmontools**

**sudo smartctl -a /dev/hda**  (or sda, etc)

run a long (or short) test to see if it checks out.

Or just skip to formating and installing.

Get [Darik's boot & nuke]("http://dban.sourceforge.net/") or Active Killdisk and wipe the drive clean.  

On the ubuntu live cd use Gparted (system>admin>gnome partition manager) to create an ext3 and swap partition on the other half of the disk.  Then go through the install steps and put ubuntu there.

---

### Post by Herman on 2007-09-22
Hey logos34, that's a great suggestion to try using smartmontools, I'm giving that a try myself just to see how it works. :)

Hello uncleclinto,
If you are usiig the 'Alternate' CD because you can't use the Ubuntu Live CD for some reason, you may still want to know how to use partman in the 'Alternate' CD for doing this.
Here's an excerp from one of your links,
> If you select a pristine disk which doesn't have neither partitions nor free space on it, you will be offered to create a new partition table (this is needed so you can create new partitions). After this a new line entitled “FREE SPACE” should appear under the selected disk.               If you select some free space, you will be offered to create new partition. [COLOR=Sienna]**You will have to answer a quick series of questions about its size, type (primary or logical), and location (beginning or end of the free space).**[/COLOR] After this, you will be presented with detailed overview of your new partition. There are options like mountpoint, mount options, bootable flag, or way of usage. If you don't like the preselected defaults, feel free to change them to your liking. E.g. by selecting the option Use as:, you can choose different filesystem for this partition including the possibility to use the partition for swap, software RAID, LVM, or not use it at all. Other nice feature is the possibility to copy data from existing partition onto this one. When you are satisfied with your new partition, select Done setting up the partition and you will be thrown back to **partman**'s main screen.You would just need to select 'manual partitioning' after you get to through the usual location, keyboard, detecting hardware and so on. 
 
Now, assuming your hard drive is all 'free space', (has no partitions in it at the moment), you will just need to create a 8.8 GB partition in the free space. Then you'll be asked if you want to partition to be created at the beginning or the end of the free space, and you choose the end.
Then make a swap area of 1.0 GB and place that at the end also, (At the end of the free space, so it will be in front of your  main '/'  (root) Ubuntu partition.
...or, you could make your swap area first if you want it at the end of the disk for some reason. It wouldn't matter at all. 

You can make the swap area smaller if you want, 1.0 GB is a generous size for a swap area, half that would probably be enough. 

It doesn't matter if your swap area is a primary partition or a logical partition (inside an 'extended' primary partition), most of us have logical swap areas because that's normally the default if we let the installer do the partitioning for us automatically.

This link contians some illustrastions about how to use the 'Alternate' CD and Partman partitioner: [Ubuntu+NTFS]("http://users.bigpond.net.au/hermanzone/p3.htm")[COLOR=#000000] ,look in my sig links for more about the 'Alternate' CD. 
Regards, Herman :)
[/COLOR]

---

