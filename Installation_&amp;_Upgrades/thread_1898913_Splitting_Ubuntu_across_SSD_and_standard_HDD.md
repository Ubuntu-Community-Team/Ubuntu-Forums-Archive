---
title: "Splitting Ubuntu across SSD and standard HDD"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by christopher.mountford on 2011-12-22
hi was just wondering if anyone could tell me if it is possible to split the different areas in the Ubuntu file system across disks. 

I am building a new computer and want to minimize read/write cycles to the SSD so I was thinking of using the SSD as a drive for the system files (such as lib, sys, selinux)  and using the standard hard drive for everything else (such as tmp, usr, home). Is it possible to split the system like this? and how do I do it? I haven't built my new computer yet but would like to know beforehand so that I don't run into problems

---

### Post by Lars Noodén on 2011-12-22
It's possible to split things up as you want them to be split up.  The system doesn't really care what kind of media you use.

The only constraint that I can recall is that / and /etc must be on the same partition.  If you want to see what is where look at the manual page for [hier](http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html)

/proc, /sys, /dev and /run are already mounted as RAM disks.

Of the others, only the directories /home, /var, /var/tmp, and /tmp are likely to be written to.

---

### Post by oldfred on 2011-12-22
I want my SSD to have all the system files, so system runs faster. Data is then on spinning drive. I also keep /home on the SSD but link in all the data folders so the user settings are also quickly loaded. The Arch link notes that SSD writing 10GB per day will still last 8 years.

Some of these links are more up-to-date than others but useful info to review.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)
Tuning Solid State Drives in Linuxcheckbox
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

---

### Post by dabl on 2011-12-22
With the erase cycle specs for recent SSDs, actually wearing one out seems most unlikely.  However, like you, I was concerned, so I did put /tmp, /var/tmp, /var/log, and /var/spool on a tmpfs.  But putting /var/log on tmpfs means you lose the logs after reboot, so maybe you want to run the new system for awhile and make sure everything is solid before you add a line to /etc/fstab to change that.  One of the easiest things to do is to change the ext4 mount options to slow down the journal-writing, from the default 5 seconds to something long -- I use 120 seconds.  Here is my /etc/fstab file:

```
UUID=bea3a748-3411-4024-acd0-39f3882ddaf9     /                    ext4         defaults,noatime,errors=remount-ro,discard   0    1   
UUID=8cfe2acc-7572-4b45-b25f-ed021bb1d78b     /mnt/SDA2            ext4         defaults,noatime,discard                      0    0   
UUID=ec21f5b3-7fd4-4f4b-af8d-cf787b147ae8     /mnt/REVODATA        ext4         defaults,noatime,discard                      0    0   
           0    2   
UUID=0d939b7d-48f1-47dd-aebe-77e7bd8c3503     none                 swap         sw                                            0    0   
none                                          /tmp                 tmpfs        defaults,noatime,mode=1777 0 0
none                                          /var/tmp             tmpfs        defaults,noatime 0 0
none                                          /var/log             tmpfs        defaults,noatime 0 0 
none                                          /var/spool           tmpfs        defaults,noatime 0 0
```

Here are some links with useful information:

[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226&viewfull=1#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226&viewfull=1#post373226)

[http://www.cyrius.com/debian/nslu2/linux-on-flash.html](http://www.cyrius.com/debian/nslu2/linux-on-flash.html)

[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

[http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190](http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190)

Hope this helps!

---

