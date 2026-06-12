---
title: "Dual-boot/repartitioning question before installing"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by crisnoh on 2007-09-30
I'm getting ready to install Ubuntu on my Desktop PC and after defragging my hard drive I found that Windows has managed to completely spread files and crap across the hard drive in such a way that there is barely enough hard drive space in any one contiguous section to install Ubuntu.  Just to let you know what a monumental feat this is keep in mind that the size of the partition in question is 226GB, 196GB of which is free space.

My question is, during the installation process, when the repartition options come up and I decide how much space to allocate for each OS, will my files be rearranged into their correct partitions or should I find some other solution to my dilemma lest my beloved music collection be deleted?

---

### Post by dabl on 2007-09-30
I'm not sure what evidence you are relying on to conclude that your Windows files are so scattered. You should run "Disk Cleanup" once, and then "Disk Defrag" about 3 times, and then you should have a pretty contiguous Windows file system -- that's as good as it will get.

I like to use the free GParted Live CD to look at the hard drives and do the partitioning, before even booting the *buntu Alternate Install CD (which I recommend over Live CD for installing dual boot).

Get the GParted Live CD ISO here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

With GParted running, you can use the graphical interface to highlight your partition, shrink it to make space for Ubuntu, and then make new partitions for Ubuntu.  I like to make 3, one each for /, /home, and swap.  Make / about 6GB, swap about 0.5GB, and the rest for /home. :)

---

### Post by Pumalite on 2007-09-30
Defrag multiple times, the more times, the better. Then in Vista, use the Vista partitioner. In Xp, use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
(the stand alone, burn to CD, boot from, program)
Boot from it, right click XP partition and in the menu choose 'resize partition'

---

### Post by wetland on 2007-09-30
I would also suggest backing up all important data just in case something goes wrong all though (not likely ). I will third the gparted utility. I have installed Linux 50 plus times only had a problem once. I did have my backup data.

---

### Post by crisnoh on 2007-10-02
Ok, I was getting the fragmentation feedback from disk defragmenter after having run it a couple times.  After going through the defrag process about 8 more times, and then dealing with a fragmented paging file manually, I'm left with a still fragmented Master Table File that according to the info I got on MS's website is unmovable.  So I guess the question now is, will the partition editor just move that into it's correct partition when run and if not do I care if the MTF get's wiped?

---

