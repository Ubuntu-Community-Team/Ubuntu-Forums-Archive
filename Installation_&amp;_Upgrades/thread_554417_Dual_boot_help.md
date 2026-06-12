---
title: "Dual boot help"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by gmg27 on 2007-09-19
Hello board, I'm an ubuntu newb and I need some help. I have Vistas and I read somewhere that you shrink your windows partition and Ubuntu will install over the free space. Well I goofed and created a second partition ( F partition). When I installed Ubuntu, it completely ignored the F partition and shrunk the Windows partition again. 

I tried to delete the (F partition) and something went screwy. Now when the GRUB loads up it displays "Error 7".

Here are my questions. What did I do wrong and how can I fix it? It's a brand new computer so I don't have any important data to lose. I have an 80 gig hard drive and I want to divide it into 3 partitions :40 gigs Vistas, 30 gigs Ubuntu, and 10 gigs recovery drive. How can I accomplish this?

Thank you in advance.

---

### Post by confused57 on 2007-09-19
If you have a Vista install DVD(not a restore disk), you can use the bootrec.exe utility to restore Vista's IPL to the mbr:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you don't have a Vista install DVD and have access to another computer, I would recommend you download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD may be able to restore your Vista boot

Once you're able to boot into Vista, then you could Vista's built-in partitioner to resize your Vista partition and create "unallocated" space by deleting your current Ubuntu partitions:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

In the event you're not able to accomplish the above, you might want to try reinstalling Ubuntu; but be sure to select "manual" partitioning and install over your current Ubuntu install or select the space created when you deleted the "F" drive partition:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Hopefully, after reinstalling Ubuntu you'll have an entry in grub to boot into Vista...there is a utility called MbrFix.exe that you can use to restore Vista's IPL to the mbr:
[http://ubuntuforums.org/showpost.php?p=2809942&postcount=22](http://ubuntuforums.org/showpost.php?p=2809942&postcount=22)
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

You also could use Gnome Partition Editor in the Ubuntu live cd to delete your Ubuntu partition(s) and resize your Vista...however, sometimes there are problems when resizing Vista ntfs partitions using gparted.  An excellent partitioning tool is the gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
it has a later version of gparted and may be better able to resize Vista.

You might also consider using Vista's bootloader to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

