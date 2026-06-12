---
title: "Installing Windows XP AFTER Linux on a multiboot machine?"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by amosbatto on 2007-02-06
On my harddrive I have:
hda1 Windows XP Home (NTFS)
hda6 FAT32 
hda7 Debian (EXT3)
hda8 Ubuntu 5.10 (EXT3)
hda9 Fedora Core 4 (EXT3)

I decided to delete the hda7 partition with Debian and install Windows XP Professional in its place.  I used the Windows XP Pro installation CD to delete the hda7 partition, then created an NTFS partition and installed Windows XP Pro without any problems.  

Now when I boot up I see two options: 
Windows XP Professional
Windows XP Home

Of course crappy Windows doesn't recognize my Linux partitions, but the linux partitions still exist on my harddrive.  I have installed ext2ifs in Windows and I am able to read files in my Linux partitions with no problems.  

When I run GParted from the Ubuntu 6.06 LTS installation CD, it tells me that there are no recognized partitions on my harddrive. The same thing happens when I try to use the disk partitioner on the Kubuntu 6.10 installation CD.  What happened to all the partitions on my harddrive?  Obviously the partitions still exist, since I can boot into either Windows XP Professional or Home and ext2ifs in Windows shows the Linux partitions.  The question is how do I boot into my Linux partitions and why can't the disk partitioner in Ubuntu see those partitions?

---

### Post by orb9220 on 2007-02-06
> Now when I boot up I see two options:
Windows XP Professional
Windows XP Home

That is because xp after install writes over the mbr wiping out the grub loader, XP thinks it is the only OS in the world. To restore grub follow this.

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

