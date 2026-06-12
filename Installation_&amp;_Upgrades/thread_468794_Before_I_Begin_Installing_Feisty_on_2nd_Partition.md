---
title: "Before I Begin Installing Feisty on 2nd Partition"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by monkeyridesllama on 2007-06-09
I'm a Windows user and want to create a dual-boot WinXP/Ubuntu.  I have been using Wubi for some time now and really enjoy it, but I thought it might be time bite the bullet and install Ubuntu for real.  I have some questions before I begin.

I want to install on the second partition of my first drive (E:).  It's 12.7 GB.  I know I am going to have to do this manually but I got to that part of the installer and chickened out.  

First of all, is that going to be enough room?  
Second, how do I use the installer to fix this up for Ubuntu?  
Third, is there a way to still have it dual-boot despite the manual setup?

Thanks for any attention you give this.

---

### Post by louieb on 2007-06-09
You should be in good shape. At least you don't have to do the most dangerous step in setting up a PC to dual boot (shrink you existing windows partition). 
1st: 12 gig should be plenty of room.
2nd: [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")
3rd: how you set up partitions is separate from setting up GRUB for dual boot. (not a problem)

I could get more  specific about recommending a partition setup but first   I would like to see what your current partition table looks like. Boot to Ubuntu and open applications>accessories>terminal and run ```
sudo fdisk -l
```  (lower case  L). and post the output here. 

Check out the Dual Boot and psychocats links in signature: lots of good stuff there too.

---

### Post by monkeyridesllama on 2007-06-09
Here ya go:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7936    63745888+   7  HPFS/NTFS
/dev/hda2            7938        9598    13341982+   7  HPFS/NTFS
/dev/hda3            9599        9729     1052257+  d7  Unknown

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    7  HPFS/NTFS

```

I don't want to install it on my 2nd physical drive. Just ignore that one.

Thanks for the help.

---

### Post by louieb on 2007-06-09
If it were mine and I wanted to dual boot XP and Ubuntu.
When you get to the partitioning step choose manual partitioning.[LIST]
[*]Delete the 2nd partition this will give you 12 gig of unallocated space.
[*]Create an extended partition using all 12 gig of the newly unallocated  space.
[*]Create 3 logical partitions inside the extended partition.[/LIST][INDENT][LIST]
[*]one for / (root) 5-6 should be plenty. format ext3
[*]one for /home use all the rest but for a half gig or so. format ext3
[*]one for swap use the rest. format swap.[/LIST][/INDENT][LIST]
[*]once you sure you really want to do it click apply once you do that theres no turning back.[/LIST]Remember the names listed on the screen your going to need them on the next screen. 
The next screen is where you select the mount points for your Linux install.
Select your mount point for your newly created /, /home and swap partitions.
and optionally if you want to be able to read the data on you windows partitions you can define mount points. I haven't used the Feisty live installer so I'm a little fuzzy on using it. But the psychocats site has screen shots to refer to. 

But basicaly the mount partition part of the install need 3 pieces of information for each partition on your hard drives.       [LIST]
[*]partition name ie.  /dev/hda1
[*]mount point  ie. / or /home or /media/widows ...
[*]format it (yes or no)[/LIST]Good luck  Just be careful and read everything on each page of the installation and you  should be dual booting in about an half hour or so.

---

### Post by monkeyridesllama on 2007-06-09
Thanks!

I shouldn't have to use GParted then, right?

I'll give it a whirl!

---

### Post by louieb on 2007-06-09
> **monkeyridesllama said:**
> I shouldn't have to use GParted then, right?
The live CD installer uses a modified version of GParted  partitioner. That why I posted the documentation link earlier. Just be sure to run the media check option on the install CD before starting the install its self. Although it should be safe enough: heres the [COLOR=Red]**standard warning**[/COLOR]  backup any data, photos, music ... you don't want to loose

---

### Post by monkeyridesllama on 2007-06-09
All installed!  Thanks so much.

I ended up using GParted anyway - the interface was easier than the LiveCD Installer.

---

