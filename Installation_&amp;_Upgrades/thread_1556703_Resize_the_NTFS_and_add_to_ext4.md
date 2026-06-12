---
title: "Resize the NTFS and add to ext4"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by gavdari on 2010-08-19
Hi,
I have a dual boot system with Ubuntu Lucid and Windows 7 Ultimate 32bit on a 320 GB hard drive. During the last month, I've completely moved from Windows to Ubuntu but I have to keep Windows for a few softwares like ooVoo and Office, especially OneNote. But now 105 GB for windows and 50 GB for Ubuntu doesn't seems right, as I can't copy any more files on my Desktop in Ubuntu, because it's full. I was just wondering if it's possible to resize the NTFS partition and add like 50GB or so to the ext4 partition which is my Linux's root.  The NTFS drive is on /dev/sda5 and the ext4 one is on /dev/sda7.

---

### Post by bhaverkamp on 2010-08-19
This is definitely possible. I have done it myself many times. Gparted will do most of the work for you. I kept shrinking my XP partition to the point of disappearance.

---

### Post by gavdari on 2010-08-19
Is there anything I should back up before starting to play with Gparted?
And after starting, how can I unmount the root partition to resize it?

---

### Post by bhaverkamp on 2010-08-20
Do the GParted from a live CD; no mounting issues. Backup is a tricky issue. I have managed not to lose anything yet doing this. Backing up however is always a good idea. You have to decide what's important to you. If you screw this up you'll lose everything. Now that I have scared you; as long as you don't lose power in the middle of these operations it should just work. Make sure you've had a clean shutdown of Windows before shrinking the NTFS partition. GParted can see the dirty bit and won't touch it if it's dirty.

Good Luck!

---

### Post by drs305 on 2010-08-20
Take a look at the second half of the first post of this thread for tips/techniques:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")


The original post was written in response to a bug in Jaunty but the second half of post #1 discusses how to take space from Windows and give it to Ubuntu.

---

