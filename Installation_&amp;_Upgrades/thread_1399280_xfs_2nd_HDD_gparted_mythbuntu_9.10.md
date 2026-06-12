---
title: "xfs 2nd HDD gparted mythbuntu 9.10"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by sbrattonuk on 2010-02-05
I'm trying to format/partition my second HDD with xfs using gparted, most of the file system type options are greyed out any idea why ?

and how to resolve ?

Thanks
Steven

---

### Post by labinnsw on 2010-02-12
You need to unmount the partition before making any changes with Gparted.

---

### Post by sbrattonuk on 2010-02-14
Thanks for your reply,
I pretty sure this isn't the cure.
I can delete all the partitions on the drive so it's definitely not mounted
 
When it comes to re partitioning and formatting, I only get the option of EXT2,3,4 FAT16,32,linux-swap & unformatted.
 
hfs,hfs+,jfs,ntfs,reiser4,ufs & xfs are all greyed out.
 
My thought is that support for these filesystems has been removed from Mytbunut 9.10.  or I've set an option somewhere that stops me from selecting these file types.
 
 
Any mroe ideas
Thanks
Steven

---

### Post by labinnsw on 2010-02-14
Try it using Gparted Live or the Karmic disc.

---

### Post by sbrattonuk on 2010-02-17
getting somewhere, It must be mythbuntu 9.10 filesystem support.
 
Booting from Fedora10 live USB install on flash drive. 
I now have the extra option of ntfs which wasn't there before.
 
all the others types remain as they were before.

---

### Post by fralik on 2011-04-16
@sbrattonuk: have you managed to format your drive?[URL="http://ubuntuforums.org/member.php?u=965712"]
[/URL]

---

### Post by sbrattonuk on 2011-04-17
Yes I got it sorted.
Installing the partition manager on the mythbuntu system was sufficient to do the job.

I did need to chown -R as the mythbuntu user to make it read/writeable once formatted.

Then mount the drive as the recordings directory on the main file system.

The filesystem type also needs to be supported by the host OS. (mythbuntu). Creful if you use another means of formatting the drive (eg live CD from another distro).

Steven

---

### Post by fralik on 2011-04-17
I also managed to activate more filesystems in Gparted after I've install more mkfs packages. Seems that it is just the matter of what have been installed by default.

---

