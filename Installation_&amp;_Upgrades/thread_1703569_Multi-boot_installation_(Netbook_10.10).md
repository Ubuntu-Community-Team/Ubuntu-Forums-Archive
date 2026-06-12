---
title: "Multi-boot installation (Netbook 10.10)"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by nscherneck on 2011-03-09
Hello all,
 
I'm new to Ubuntu (and Linux entirely) and am working through all the info to do my first install. I've read through a few threads here and a couple tutorials on dedoimedo.com. I still have a few questions. I have an Acer netbook that's currently running Windows XP Home SP3. There are two partitions currently:
 
- 5Gb, FAT32 (I assume this is a restore or backup partition of sorts)
- 145Gb, NTFS (System partition where Windows lives)
 
I'd like to keep Windows in tact and install Ubuntu Netbook 10.10 and setup partitions for three other distributions (not sure which yet).
 
**Q1: Am I better off erasing the entire harddrive and reinstalling Windows? From what i've read it seems like this would be easier than trying to reduce the size of the partition containing the current Windows installation.**
 
**Q2: I'm thinking this will be my partition table:**
 
/dev/hda1 primary ntfs 15Gb windows XP
/dev/hda2 primary ext3 10Gb linux (Ubuntu Netbook)
/dev/hda3 primary ext3 10Gb linux (future installation)
/dev/hda5 logical ext3 10Gb linux (future installation)
/dev/hda6 logical ext3 10Gb linux (future installation)
/dev/hda7 logical 2Gb linux-swap
/dev/hda8 logical ext3 42Gb home
/dev/hda9 logical ntfs 50Gb data (Windows)
 
**Are there problems with this?**
 
**Q3: I understand the installation of Windows should happen first, so should I create the partitions with Fdisk at that time? If I do this can Fdisk do ext3 or will I have to use Gparted to change the filesystems of the Linux partitions after the Windows installation is complete?**
 
System Info:
Acer AspireOne
Intel Atom N270 1.6Ghz
1Gb RAM
150Gb HD
Currently running Windows XP Home SP3

---

### Post by oldfred on 2011-03-09
I think you should be able to shrink XP. I know Vista & 7 have issues and there are some work arounds. Only 15GB for windows is not a lot. Windows or NTFS partitions work best with over 20% free space and at 10% just about stop. Of course Linux partitions need free space also.

You should house clean windows, defrag probably more than once and then see how much you can shrink it.

You cannot share /home. For single installs, I recommend a separate /home as it makes it easy to reinstall. But the user config files are fairly small and most of the space is really your data. Then I suggest a separate /data. But you already have a NTFS data partition. I do have both only from when I still booted XP a lot, and now most of my data is in /data. But most of my additional installs are versions of Ubuntu so it is easy to share the /data partition. Other systems may have different uid/gid issues.

I always use gparted and usually create all partitions with a separate gparted liveCD. Then use manual install. If you are confortable with command line the Linux fdisk will create all the partitions, but not the Windows fdisk.

---

