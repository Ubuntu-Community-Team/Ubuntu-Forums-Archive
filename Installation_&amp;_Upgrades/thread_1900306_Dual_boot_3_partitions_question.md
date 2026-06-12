---
title: "Dual boot 3 partitions question"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by cowboybebop32 on 2011-12-26
So here's my problem. I am trying to set up a dual boot with Windows 7 and Ubuntu Studio. I was looking into a way to have one partion with 7 on it, one partition with Studio on it, and then one partion with my documents/music/videos. I also wanted to use that last partion to install programs on. I know i can do this from the windows side by just telling programs to install on that partition, but is there any way to also install my Ubuntu programs i get from the repos on this partition? I was hoping to make both of my OS partitions small and then use the large partition as a shared storage for the two. Is this possible? Or am I going to have to make my Studio partition larger to hold the programs too?

---

### Post by Mark Phelps on 2011-12-26
If I understand your question, you want to install BOTH Windows and Linux apps to the same partition.

Sorry, can't be done.  Each OS needs the app partition formatted using its own native filesystem.

You can share a DATA partition, but not an Apps partition.

---

### Post by oldfred on 2011-12-26
As Mark Phelps's says you cannot share apps but can share data.

I do like smaller system partitions and in Linux apps are small. A full install of Ubuntu is just over 4GB, and with many apps I have about 7GB and normally make a 25GB / (root) partition so only about 25% is used. All my  data goes into a ext3 partition or a shared NTFS partition. I keep Firefox & Thunderbird profiles in the shared NTFS partition and have the same bookmarks & emails in all the systems (most Ubuntu) I boot.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by cowboybebop32 on 2011-12-26
Ok thanks alot for the help guys. Ive decided to go 80gb of ext3 for ubuntu studio, 80gb of fat32 for storage and then the rest (around 160gb) for the windows 7. Thanks!

---

### Post by oldfred on 2011-12-26
I do not recommend FAT32 unless you have to have it for some specific reason. It really is only ok for small flash drives. It has no journal so recovery is more difficult & chkdsk takes longer, and it cannot store a file over 4GB.  Better to use NTFS if you want to share with Ubuntu & Windows.

---

