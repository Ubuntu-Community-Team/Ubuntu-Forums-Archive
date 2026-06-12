---
title: "Upgrade from 8.10 to 9.04 adds 7 GB to disk"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by bsalem on 2010-11-11
I want to get to a supported release from 8.10. I elected to do the upgrade to 9.04, which is still not supported, and hope eventually to get to 10.04 LTS, which is. 

I have a 35 GB partition with my home files on it, bad mistake given that Ubuntu needs frequent updates, if I had to do it over again I would make a separate partition for my files and mount that on /home.

The issue I have is that the upgrade packages amounted to 7 GB and the upgrade should have released
about that much in space when it cleaned up postinstall, it did not. Should it have reclaimed that much?

The sweeper and other clean up tools do not work well, they are especially dangerous with with third party apps like Google Chrome, which I had to reinstall.

Looking around on my file system I noticed that /usr/lib had grown to over 4 GB and that it appeared that
older versions of libraries and etc. were hanging out.

What can break the cleanup step and is there any recommended way to clean up after this mess?

It makes me leary of trying to do any further upgrades. It seems that repartitioning to separate my home dir from the rest of the system is the best approach and to do reinstalls instead of upgrades.

That said, let me register my disagreement with the support policy, the fact that after a year versions of ubuntu fall out of support, and that upgrading is costly.

Perhaps installing ubuntu by default with two prtitions one for /home and one for / would make this easier, one could just replace the root partition each time a new release has to be installed.

It would really be nice if releases were supported for a longer time, as compared to other Linices and
OSs like Mac OSX.

Bruce Salem

---

### Post by houseworkshy on 2010-11-11
One can upgrade but the general opinion I get when browsing around this forum is that it is better to do a clean install from a cd.  10.04.1 is smaller than that and will be supported untill 13.04 which is quite a while.  It is also worth searching for guides on putting ones home in a seperate partition so that one can clean install whilsts leaveing ones documents, videos etc intact.

---

### Post by snowpine on 2010-11-11
I'd strongly recommend a backup of your documents, followed by a fresh reinstall of 10.04 with your /home on a separate partition. Lucid Lynx 10.04 is a "long term support" release (36 months), designed specifically for people who don't want to update every 6 months.

You might also consider a different distro. There are two extremes:

1. A "rolling release" distro (like Arch) has no distinct releases. You get a steady stream of application updates as they become available, so theoretically you never need to reinstall,  you just keep rolling.

2. An "enterprise" distro (like Red Hat) will have a very long support cycle... I believe it's 10 years for Red Hat, if you pay them enough. :)

Ubuntu tries to be a good compromise between those two extremes, offering from 18 months (regular releases) to 5 years (LTS server) of support.

---

### Post by oldfred on 2010-11-11
Several versions of moving /home.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I have 3  root partitions of 20GB. Last , current & beta to test until I make it current. I now include /home in root as I have all my data in /Data partition that I mount in every install.

I back up any config files I change in /etc in case I need the old settings (not always needed). And I make a list of installed apps to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by bsalem on 2010-11-11
Thanks to all for your quick replies.

Oldfred: Thanks to you for the refs on partitioning. I will study those pages because I'd like to rob space from the Windows partition I have and possibly move two expendable partitions that have ext3 filesystems on them. I am worried about the partition numbers getting changed and grub being able to figure out what changed. I figure the partition for /home needs to be around 20 GB which I could rob directly from the NTFS partition if I need to. Then move the files on /home from the Ubuntu root to there.

The concerns I have are that Windows Vista and another ubuntu live in the windows partition and that that NTFS may need to be defraged before I bight 20 GB out of it, It has much more than that of free space. The filesystem hasn't had lots of changes, Is the partition program smart enough to take the space I need and do the equivalent of a fsck on the NTFS partition? This is answered in the links you posted. Gparted should be able to do this on its own.

The other way to go about this is to merge the noncontiguous ext3 partition spares into one. I remember that there were partition programs that could combine partitions and move around the others. Am I dreaming? Again, my examination of the links you sent suggests
that this is possible.

I had made a backup of my files before I messed with the upgrade.

That leaves only one issue, that grub could be confused about which partition to boot
from.

---

### Post by oldfred on 2010-11-11
With Vista & 7 it is better to shrink them with their tools in MMC. Some times when gparted is used major repairs have to be done to get them working again. Even after windows resizes itself it will want to run chkdsk or other repairs.

If only resizing partitions the numbers & UUIDs do not normally change. If they do then you have to reinstall grub2 & possibly edit fstab.

You cannot combine standard partitions. I believe LVM lets you move things around easier but I do not like the extra layer of complexity. LVM would require total reinstall I believe. 

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

### Post by bsalem on 2010-11-12
Thanks again for the info on LVM and resizing NTFS under Vista, my instincts tell me to resize that FS under its native OS. 

/dev/hda1 if the Vista partition, of course.
/dev/hda2 is a factory installed backup of cab files for Vista.on the high cylinders of the drive
/dev/hda3 is a small EXT3 whose cylinders are adjacent to /dev/hda1

the extended partition /dev/hda4 has all the remaining partitions.

If I use Vista to shrink /dev/hda1, can I grow /dev/hda3 into the unused space? What is
on it is expendable, that would involve allocating cylinders that were once part of the
Windows partition to /dev/hda3 and recreating an EXT3 fs on that partition, I could
make it reasonably large for a boot partition, and then use the existing Ubuntu boot
partition for /home, that is mount /dev/hda7 on /home in /dev/hda3 with U 10.02 LTS
installed on it. The two little partitions are /dev/hda6,8 I think and there are a couple
of small swap partitions. I can just leave these alone for now.

Also, does it matter to you when I mark this as solved? I could do so now before trying the many fine choices you have indicated. If the usual practice is to close a ticket if some fix has been offered by not tried, then lets close it now, and if the fix causes a new problem, then open a ticket specific to the new issue.

I tend to mull over these things a bit.

---

### Post by oldfred on 2010-11-12
The only advantage of solved is that other users with similar issues will possibly see your title and then know that something worked, so they will review it. 

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

---

### Post by TBABill on 2010-11-12
I wouldn't mark solved till it really is. Keep asking related questions till you get the appropriate answers. You can't go wrong asking and learning more to get the proper perspective. (suggestions only...do what you feel is best)

Do you have the ability to download and burn the CD to get a copy of 10.04 or 10.10? If not, do you have the means to order one for free from Ubuntu? You can move those files to a safe place, then install right on your current Ubuntu partition. So much easier and much less downloading this way than upgrade after upgrade to get to a supported version.

---

