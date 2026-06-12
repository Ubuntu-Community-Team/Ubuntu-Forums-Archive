---
title: "NTSF to ext4 problem"
date: 2013-02-05
forum: Installation &amp; Upgrades
---

### Post by pbhill on 2013-02-05
While performing a fresh install I inadvertently changed an 500 Gb NTSF drive to ext4. I had used that drive when booting into Windows. Now it appears that I have lost the data on this drive. If I change it back to NTSF, will my data be visible or has it been deleted? What is the best filesystem to use for data storage when dual booting? Any suggestions?
Thanks in advance.

---

### Post by SeijiSensei on 2013-02-05
> **pbhill said:**
> If I change it back to NTSF, will my data be visible or has it been deleted?

Probably, but if you have never touched the drive at all since it might be recoverable.  Otherwise you'll need the services of a professional data recovery house which will cost serious money.

>  What is the best filesystem to use for data storage when dual booting? Any suggestions?

Linux can read and write to NTFS; Windows knows nothing about ext4.  If this is solely a data storage device and not a boot device, then use NTFS.  If it is the boot drive, you might consider creating a separate partition for data storage and putting NTFS on it.  It will appear as D: or E: or whatever in Windows; in Linux you need to mount it by following [these steps]("https://help.ubuntu.com/community/MountingWindowsPartitions").

---

### Post by pbhill on 2013-02-05
Thanks for your reply. Another question... when assigning mount points to the various drives/partitions, I can't use the same mount point more than once. What if one has four or five hard drives, all NTSF, what should I use for mount points?
thanks.

---

### Post by SeijiSensei on 2013-02-05
Just create them with mkdir.  Traditionally /mnt was the place to mount things, but lately /media seems to be the norm for long-term mounts, and /mnt recommended for temporary mounts.  Using /mnt for illustration:

```

cd /mnt
sudo mkdir p1 p2 p3 p4 p5
sudo mount /dev/sdb1 p1
sudo mount /dev/sdb2 p2
[etc.]

```

---

### Post by Mark Phelps on 2013-02-06
IF you just change it back to NTFS, the partition table has already been blanked -- so it will seem like an empty partition.

What you could TRY is the following:
1) Download and burn the Minitool Partition Wizard Boot CD.  This is an MS-Windows based partitioning tool
2) Boot from the CD and see if it will allow you to select the partition recovery option.  If so, try that option
3) Then see if you can now access the files on that partition.

If that doesn't work and you STILL want to get to the files on that former partition, post back because you will need to do something different.

And, in the interim, do NOT mess around with this drive using Linux utilities -- that can make the files unrecoverable.

---

### Post by pbhill on 2013-02-12
I ended up using Photorec to recover a lot of files. Some were corrupted, but I'll consider it a lesson learned! The problem I have now is that none of the recovered files have their original names, and are named with a series of numbers/letters. I have several thousand music files and it would take me years to manually edit them! Rhythmbox seems to know what the tracks are however. Is there a program that will rename the recovered files?

---

### Post by isaquealves on 2013-02-12
Sometime ago, i suffered with a simillar case. *Testdisk* helped me to solve that trouble. A tip for you: maintain a* MBR backup* of you disk and try to give good labels to your partitions, so, you will not to be confused anymore.
For the renaming music files task, you could try *easytag*... it support batch tag editing, and the task or rename them will not be so annoying...:o

---

### Post by Alcidious on 2013-02-12
I had a problem where I almost lost all my data I keep on an external HDD. I only switched to linux a year ago, and in my ignorance I kept backing up and copying files to the hdd, which was formatted in ntfs.

During a backup, My computer froze, and when I rebooted all my data was gone!  So what I did was I used a friend's computer, who had windows, and I used the windows recovery tool. It was a lot of data, so it took a whole evening, but it was all restored. 

So I downloaded all of that onto my linux/ext4 hdd, then re-formatted my external hdd to ext4, then transferred all the files.  

Don't know if that will help, but I thought it might. Good luck

---

### Post by fdrake on 2013-02-12
for renaming try [http://www.howtogeek.com/howto/21245/tag-and-rename-music-with-tagscanner/](http://www.howtogeek.com/howto/21245/tag-and-rename-music-with-tagscanner/)

best filesystem to use while sharing data among linux and windows is either fat32 or NTFS.

remember that you can fix/recover data written on wind partition with chkdsk d: /f  (where d id the drive unit recognized by windows)

---

### Post by oldfred on 2013-02-13
When I used photorec, I was recovering text files. It also found all the backups so I had many test files and many versions. It was a lot of work to sort thru. I now include the name of every text file in the text file.

       Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

