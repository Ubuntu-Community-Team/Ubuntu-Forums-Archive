---
title: "Problem with HDD partitions"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by Bhushan1408 on 2013-06-23
Hello everyone i am new to linux. I installed windows 7 on my laptop with 2 partitions and 50 free space for Ubuntu 12.10. When I started setup for Ubuntu I choose replace Ubuntu with windows 7. 
Then I have completed setup I upgraded it to 13.04. And now I can not see any partition which I have created in windows. Please help me to get those lost partitions back.

---

### Post by oldfred on 2013-06-24
I am not sure I followed the order you installed thing in? Replace Ubuntu with Windows?

Windows will not see Linux formatted partitions.

From liveCD, in case you overwrote something we do not want activity on hard drive.

From terminal copy & paste this to see all your partitions. If you have more than one drive run again for sdb.

       sudo parted /dev/sda unit s print

---

### Post by Bhushan1408 on 2013-06-24
I am extremely sorry
I have chosen the option 
'Replace windows 7 with Ubuntu' this is what I wanted to say

---

### Post by oldfred on 2013-06-24
Then you erased Windows as that totally replace everything on hard drive. It had RED waring that everything would be erased.
If you had other partitions you wanted to keep, then you needed to use manual install.

If you did not have good backups, you can use testdisk to see if it sees old partitions. You may be able to recover some data. 
If testdisk does not work then you can use photorec. I have used photorec. It is a long slow process, you must have another drive with lots of room as it writes everything to new drive including previously deleted data. I have saved some files many times & it found all of them, but I never was sure which was last saved.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

      
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

