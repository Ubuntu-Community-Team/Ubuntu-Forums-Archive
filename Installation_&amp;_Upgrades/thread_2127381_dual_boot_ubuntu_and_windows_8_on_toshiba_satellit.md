---
title: "dual boot ubuntu and windows 8 on toshiba satellite"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by adhamj90 on 2013-03-19
Hello,
i really hope this question hasn't been asked, i looked around and couldn't find the same problem. if so, please direct me to the thread that talks about it. 

I have a toshiba satellite with windows 8 installed on it. and i want to install ububtu 12.10 as dual boot, so i divided the hard disk in another NTFS partition so i could install ubuntu on the new one.
the live cd works fine, but somehow ubuntu can not mount the hard disk, so i cant see the files from the live session. and when i try to install ubuntu it does not detect any other operating system. but it does detect all the partitions of the hard disk (the two main ones, plus the backup partitions for windows).i want to choose the option to install ubuntu along side other operating system, because i don't want to risk messing something up and losing the files i have on the hard disk.

i would really appreciate the help, thanks in advance
Adam

---

### Post by SeijiSensei on 2013-03-19
Ubuntu needs to be installed on a filesystem that supports Unix (actually "POSIX") filesystem attributes like permissions.  NTFS won't work.  So just let Ubuntu install itself into the empty partition.  It should reformat it to ext4.

If you want to do this manually, run something like gparted in "Try Ubuntu" mode.  Depending on the number of primary partitions you have, you might want to consider making the empty partition be an "extended" partition so you can have an arbitrary number of logical partitions on the drive.  I'd set aside a partition for swap as well.  The usual standard is 2X physical memory.

---

### Post by adhamj90 on 2013-03-19
thanks for the reply, but why cant it mount the hard disk and open it to see the files in it? ive always used ubuntu live sessions and never had a problem like this. 
if i re-allocate the new partition from windows to ext4, would that work just fine and ubuntu would be able to detect windows and install itself along side windows? thanks

---

### Post by SeijiSensei on 2013-03-19
Have you been using "WUBI" in the past?  That runs Ubuntu as a virtual machine within the Windows environment.  For a native Ubuntu installation, you need a POSIX filesystem.  

During installation, you can select manual disk partitioning and select exactly how you would like Ubuntu to handle your partitions.  You'll see them all listed along with their filesystem types.  If you select the NTFS partition, the Ubuntu installer will offer you the option to mount it as /dos or /windows and will set up the required entries in /etc/fstab to handle that.  Then you can boot into Ubuntu and still use the Windows files.

---

### Post by adhamj90 on 2013-03-19
i havent been using wubi.
and this is how ive always installed ubuntu, all i want to know is why cant it mount the disk from the live dvd this time. and why cant ubuntu detect the other operating system.

---

### Post by oldfred on 2013-03-20
If system came with Windows 8 pre-installed you have UEFI  with secure boot and gpt partitions. 

If an UtraBook it will also have a small SSD with Windows cache and that is Intel SRT that uses RAID. That can make it not see partitions.

Post this from live installer's terminal:
       sudo parted /dev/sda unit s print

---

### Post by adhamj90 on 2013-03-21
thanks for the reply oldfred, 
ill post the results of what you asked as soon as i could, since the laptop im doing this on is for work.

---

