---
title: "(g)parted vs fdisk"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by rpm13 on 2011-02-24
I generally find (g)parted more convenient than fdisk.  However recently when copying over a windows partition gparted showed it as ntfs whereas fdisk showed it as 'linux.'  

['l' option of fdisk: ntfs is 7, linux is 83]

I could not find the corresponding option in parted or gparted.  So I changed it in fdisk and it started working.  So is it that fdisk can do something that (g)parted cannot?  Or am I not finding the options?

The other thing is the inconsistency:
Use gparted and align on cylinder boundary, yet fdisk says:
Warning: partition not on cylinder boundary, and parted does not give the option at all -- just says 'not optimized for performance'.

---

### Post by srs5694 on 2011-02-24
> **rpm13 said:**
> I generally find (g)parted more convenient than fdisk.  However recently when copying over a windows partition gparted showed it as ntfs whereas fdisk showed it as 'linux.'  

['l' option of fdisk: ntfs is 7, linux is 83]

I could not find the corresponding option in parted or gparted.  So I changed it in fdisk and it started working.  So is it that fdisk can do something that (g)parted cannot?  Or am I not finding the options?

Tools based on libparted, including GParted and GNU Parted, don't give direct access to certain partition features, including the partition type code. In the case of the partition type, libparted looks inside the partition to try to identify the filesystem it contains, and it presents that information, ignoring the type code in the partition table. When you create a new partition or put a new filesystem on the partition, libparted adjusts the type code appropriately, but this detail is hidden from users. If the type code doesn't match the filesystem type, this disconnect in libparted can cause problems.

In your specific case, it's not clear to me precisely what happened -- was the type code incorrect on the original partiton, or was it not reset to the correct value on the copy? In either case, GParted and parted didn't provide you with sufficient flexibility, but fdisk did. There are other cases where fdisk can provide better control, but they're mostly very obscure -- setting unusual partition type codes or changing the CHS geometry, for instance.

IMHO, a bigger problem with libparted-based tools is that they're very sensitive to damaged partition tables. Tools such as TestDisk and the Windows installer can create invalid partition tables in certain situations, and libparted-based tools usually choke on these, claiming that the partition table is empty. You can correct such problems using fdisk and related tools, although you need a fair amount of expertise to do it. GParted and parted are useless in these situations; they won't even display the current (bad) partitions so that you can re-create them (with fixes) manually.

> The other thing is the inconsistency:
Use gparted and align on cylinder boundary, yet fdisk says:
Warning: partition not on cylinder boundary, and parted does not give the option at all -- just says 'not optimized for performance'.

This area is a bit of a mess because we're undergoing a transition from the old style of alignment on "cylinder" boundaries to the new style of alignment on 1 MiB boundaries. The options related to these features tend to be a bit buggy or unreliable, and they're changing a lot from one program version to the next. IMHO, I think that fdisk complains a lot more than it should and both tools should default to 1 MiB alignment unless you reset it to something else. The "not optimized for performance" message is confusing; it's too vague to be useful to experts and it's so broad that it scares the uninitiated. (If you're part of the vast majority that doesn't understand these issues, see [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for IBM developerWorks about it -- but be aware that the article is about a year old, which is old enough that it doesn't reflect the current state of most of the partitioning tools.

---

### Post by rpm13 on 2011-02-25
> **srs5694 said:**
> Tools based on libparted, including GParted and 


This area is a bit of a mess because we're undergoing a transition from the old style of alignment on "cylinder" boundaries to the new style of alignment on 1 MiB boundaries. The options related to these features tend to be a bit buggy or unreliable, and they're changing a lot from one program version to the next. IMHO, I think that fdisk complains a lot more than it should and both tools should default to 1 MiB alignment unless you reset it to something else. The "not optimized for performance" message is confusing; it's too vague to be useful to experts and it's so broad that it scares the uninitiated. (If you're part of the vast majority that doesn't understand these issues, see [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for IBM developerWorks about it -- but be aware that the article is about a year old, which is old enough that it doesn't reflect the current state of most of the partitioning tools.

Thanks for that link:
One thing I did not find (in a first reading) is how do I figure out
(using any tool) whether a new disk is a 4096 type of a 512 type disk?

---

### Post by srs5694 on 2011-02-25
> **rpm13 said:**
> Thanks for that link:
One thing I did not find (in a first reading) is how do I figure out
(using any tool) whether a new disk is a 4096 type of a 512 type disk?

That's trickier than it should be. Many (perhaps most or even all) of the current Advanced Format disks don't report themselves as such to the OS, even though there are protocols for them to do so. Thus, software can't identify such disks in a reliable way; the only way for software to do so would be to have a directory of all Advanced Format disks and refer to that. Such a directory would be a nightmare to maintain, and I don't know of any open source software that makes the attempt.

Thus, the best practical advice at this point is to assume that any new disk uses Advanced Format technology and partition it accordingly. If you've already partitioned a disk in a suboptimal way (for Advanced Format), the best advice is to ask the manufacturer. Most Advanced Format disks today are made by Western Digital, although I've heard of such drives from one of the smaller (in the disk industry) manufacturers -- Samsung or Toshiba or something (I don't recall which one), and talk last year was that other big manufacturers would be going this route in 2011. WD makes it pretty obvious which of their disks use Advanced Format technology on their Web site, and their Advanced Format disks also have physical labels on them, so you can identify them by looking at them with your eyes.

---

