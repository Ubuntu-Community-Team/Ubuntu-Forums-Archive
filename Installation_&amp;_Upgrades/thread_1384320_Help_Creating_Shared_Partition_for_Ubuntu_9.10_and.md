---
title: "Help Creating Shared Partition for Ubuntu 9.10 and Win 7"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by viper3ez on 2010-01-18
i already reserved the space  for the partition, from what i have read so far, it has to be FAT32 or NTFS. can someone please let me know which one is preferable?

also my major question is how i would be able to point both OS to save my files to the 3rd partition i am creating for sharing. cos in my experience, windows likes to store files in its home partition without even giving u an option to see other partitions in ur system, ubuntu at leastb allows me see the other partitions on the drive.

thanks

---

### Post by phillw on 2010-01-18
Hi,
to carry out a pain free installation - make the area for the Ubuntu installation no file system - i.e. Free Space - no file system (FAT / NTFS etc.)

As for your shared data area - the easiest is NTFS, which Ubuntu can read and write to - It's possible to teach Win about ext, the file system Ubuntu uses - but, it's much easier to just use NTFS :)

Regards,

Phill.

---

### Post by viper3ez on 2010-01-18
> **phillw said:**
> Hi,
to carry out a pain free installation - make the area for the Ubuntu installation no file system - i.e. Free Space - no file system (FAT / NTFS etc.)

As for your shared data area - the easiest is NTFS, which Ubuntu can read and write to - It's possible to teach Win about ext, the file system Ubuntu uses - but, it's much easier to just use NTFS :)

Regards,

Phill.

thanks Phil, any idea how i can direct windows to that shared space? cos windows does not seem to see my other partitions on my HD

thanks 
Nuvie

---

### Post by oldfred on 2010-01-18
Fat also has a max of 4GB per file and is not journalized so file failures are not recoverable.

windows will not see the ext3 or ext4 partitions but should immediately add a d: or f: (or some letter) drive for the NTFS partition.

I put firefox and thunderbird profiles on the shared and used the same info from both in either system. I also had photos in the shared and picasa from either windows or Ubuntu read the files just fine. I did not make windows use it as my documents but did create a bat file to copy files from c: to f:, that was I was creating a backup before I copied them to a DVD for archiving.

---

