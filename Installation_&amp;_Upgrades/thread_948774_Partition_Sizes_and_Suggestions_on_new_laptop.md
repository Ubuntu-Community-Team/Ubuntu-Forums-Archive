---
title: "Partition Sizes and Suggestions on new laptop"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by jimmyray on 2008-10-15
I searched this site but found no very recent posts answering these questions.

Just called newegg and the new laptop is on the way with a 320G drive and pre-installed Vista. Will likely keep Vista despite the fact I haven't spent much time in windoze for about 10 years. Have no idea how much space Vista will need.

Have partitioned disks since Slackware 3.something. This will be my first Ubuntu install (actually Kubuntu since I like KDE.)

Questions:
1. Plan for partitions? What would you guys suggest? Thought I'd just have a root (/), /home and /swap. 
2. What are some suggestions on the sizes? Will have some entertainment files on this laptop (mp3's,video etc...).
3. Can Vista read a ext3 drive or should I keep common files like documents on a separate NTFS partition labeled common or something and just use it to write files from linux to this drive? In the past the performance of writing to a NTFS drive was an issue but then again I have been using very old and limited hardware.

I have been reading all the articles on dual booting Vista and Ubuntu and it doesn't seem that horrible to set up.

Thanks for the time.
jimmyray

---

### Post by Pumalite on 2008-10-15
First of all allocate space for Kubuntu with the Vista partitioner first. Ahter that; you can use Gparted Live CD and make 3 'New' partitions in that free space:
10 GB for '/'
The rest minus your RAM for /home
The size of your RAM for /swap
You can make Vista deal with an ext3 partition with this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by jimmyray on 2008-10-15
Thanks for the quick reply. Makes sense.

---

### Post by sokopok on 2008-10-15
I suggest you use RAM*1.5 for swap. You could get in trouble with suspend to RAM if you suspend with completely filled RAM (you need a tiny bit more than the actual memory for suspend).
I run Vista x64 on a 40GB partition (just when I need a reminder why I love Linux so much though).

---

### Post by Pumalite on 2008-10-15
He is right. 1.25 will do.

---

