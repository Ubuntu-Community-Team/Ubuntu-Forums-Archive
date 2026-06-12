---
title: "Ubuntu_Partition Magic &amp; WinXP Newbie"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by Keats on 2006-11-23
I'm asking for help here because, after over 4 years of trying to install various Linux distros I finally got one to work, Ubuntu 6.10, - from the live CD - with Windows(Home)XP SP2.

But when the partitioning was checked, with Partition Magic, - Ubuntu had stubbornly refused to use the last part of the disk which I had reserved for it - PM claimed that there were boundary errors which it could fix. I allowed it to do so, without apparent problems but, on attempting to reboot, neither OS would oblige.

This led to a catalogue of errors. I did not want to reinstall Windows because my data would be gone (yes, I know, *backups*), so handed the problem over to a 'pro' who FUBAR'd everything and left me with an educational week of formatting, partitioning, reinstalling and exploring the hitherto untouched areas of file permissions and use of the recovery console. Not an experience I wish to repeat.

From googling, and this experience, I have the distinct impression that it is not a good idea to have two partition managers working on the same disk, so I want to stick with Partition Magic in preparing for another installation of Ubuntu.

My existing partitions (80 GB disk) are as follows, i.e. roughly the same as they were before the big brouhaha:-

    C: NTFS 14896.2 MB Primary
Extended    61420.4 MB Primary
    F: NTFS  9993.5 MB Logical
    G: NTFS 10425.0 MB Logical
    I: NTFS 15006.0 MB Logical
Unallocated 25995.8 MB Logical

I want to use the unallocated space for Ubuntu with (say) 6GB for root, 1GB for swap and the rest for Home where, once I know enough about Linux, I will keep everything which can be shared by Windows after Ext2IFS has been installed.

My questions are:-
(1) Does this seem like a reasonable allocation of space?
(2) Would it be best 
	(a)to create a single Ext2 partition after C:  using all the unallocated space, then sub-divide it as above? 
	(b)create separate partitions spread over the disk, as Ubuntu did when offered the whole disk to play with?
	(c) does the order of the partitions matter?

(3) The live CD does not include an option to use existing partitions, so how do I force it to do so when I'm finished without any further partition management? There are a further 4 disks in the distro; would any of those provide an alternative means of achieving this?

Sorry to be a wimp about this, but the last couple of weeks have been very annoying, although informative, so any help and advice you can offer would be greatly appreciated.

Tony.

---

### Post by cotcot on 2006-11-23
You should use the Alternate InstallCD. 
There is not enough info to reply your questions about the location of the new partitions. Can you have a look with "Gparted" from the liveCD ? (or from the excellent GParted LiveCD)
I guess you to not want to move partitions. And I also guess the unallocated space is at the end of the extended partition. The split you have in mind seems good to me. You could make these partitions with the GParted LiveCD and let the Alternate Install CD you these partitions.

---

### Post by Keats on 2006-11-24
Thanks cotcot. Gparted shows exactly the same partition information as Partition Magic, which I detailed in my post.

Unfortunately, everything has to go on the back burner now,until the pc is replaced because of an untraceable, persistent hardware fault. I seem to be doomed to a Linuxless life! Still, the intervening time can be spent on further research.

---

