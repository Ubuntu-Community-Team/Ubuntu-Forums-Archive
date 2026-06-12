---
title: "Partition a drive without a 'cleanly' defraging"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by imran7567 on 2007-07-13
Hey, I am new as you can see by the post count so bare with me please. I am trying to install ubuntu on a windows machine without erasing the windows content. As I understand it, I can use the free space on the windows drive to create a new partition for ubuntu. The problem is my drive is kinda cluttered and shrinking it might be a problem. All the partitioning guides recommend defragging. I have done this but at this point it doesn't seem to do much. Below is a picture of my disk. As you can clearly see the end of the disk is not 'free' in space. When I run GParted to shrink the windows drive I get an error. I am pretty sure this error is related to the fragmented files. I have run windows defragment utility atleast 10 times and Diskeeper a couple times. That is result at the bottom. My question is, can I shrink the drive to create another partition without a CLEAN disk so to speak. I want about 10 GB of space for my ubuntu install, does this mean I need 10 gb of continuous space or as long as I have 10 GB available it is OK. Thanks in advance
 
[[IMG]http://img178.imageshack.us/img178/9996/defrag1zi8.th.jpg[/IMG]](http://img178.imageshack.us/my.php?image=defrag1zi8.jpg)

---

### Post by bulldog on 2007-07-13
To cleanup your disk try to remove all un necessary programs.
You even can set your windows restore option to off and remove all the old restore points.
This should help you to clean your hdd.
Empty your explorer cache [use the clean utility in your windows] and try to defrag again when done cleaning.

---

### Post by mikewhatever on 2007-07-13
I would not dare resizing that partition. You've already tried and got an error in gparted, so, do you have another way to try it? You must have some really large files that can't get defragmented. Is there no way to free a little space?

Seconding Bulldog's post, use CCleaner to get rid of junk.

---

### Post by rillip on 2007-07-13
+1, no way that is going to give a big enough area to put a partition in.  Those fragmented files must be really, really big, or not movable for some reason, to remain fragmented at this point.  If you can't cear more contiguous space, it's a lost cause.  I'd really be looking hard at what's on my drive and identifying large files that might not be able to be moved correctly.  If you have a second disk, I'd even go so far as to say copy all the data you want over (which, by default, would make the space nonfragmented), delete it off of your fragmented drive, run defrag, then move them back over.

---

### Post by lisati on 2007-07-13
> **mikewhatever said:**
> I would not dare resizing that partition. You've already tried and got an error in gparted, so, do you have another way to try it? You must have some really large files that can't get defragmented. Is there no way to free a little space?

Seconding Bulldog's post, use CCleaner to get rid of junk.

XP's "Disk Cleanup" on the System tools menue doesn't always get rid of all the removable stuff, even when you check all the boxes.....another place to check is the "temporary" folder that can be accessed by clicking on Start->Run and typing "%temp%" (with the % but without the quotes) in the box - it's amazing how fast that folder can fill up with rubbish

---

### Post by imran7567 on 2007-07-13
Hey guys, you are all spot on. I have some really large HD Movies (6-8 gigs each). I suspected it was those files but was not really sure. I have started burning them onto DVDs. I have about 30 gigs of them still left. Just a question, how can I tell if it is safe to resize a drive. Thanks for you help guys.

---

### Post by bulldog on 2007-07-13
If you defrag two or three times ,all your files should be placed at the front of the hdd,which yu can see.
If you use the install cd to resize your windows,and it can't be done,well you know :)
But in most cases it can be done,so try and let us know.

It is recommended to backup any important file,when you gonna mess with your hdd.
You won't get a guarantee nothing can go wrong so be wise and backup!!!

---

### Post by lisati on 2007-07-13
> **imran7567 said:**
> Just a question, how can I tell if it is safe to resize a drive. Thanks for you help guys.

Rule of thumb: With backups of all important stuff made, the more free space (particularly at the end of the disk), the better.

---

### Post by Herman on 2007-07-13
I found that this link, [step by step: efficient defragging]("http://www.geekgirls.com/windows_defrag.htm#efficient") about booting Windows after a 'selective startup', without any background processes helped me defrag Windows a lot more effectively and quickly.

Here's another tip I have tried concerning the degragging of Windows.  This is not usually necessary for most computers unless you have already had problems resizing.
Windows has a thing called a 'page file'.  The 'page file' shows up as a big green unmovable block in the defragmenter. That's the Windows equivalent too our Linux swap area.  It might be a good idea to get that out of the way too, before defragging the partition. Just turn it off in 'Control Panel' -->'System' --> 'System Properties'-->'Advanced' tab -->'Performance, Settings button' --> 'Advanced' tab, 'Virtual Memory',-->'Change', [COLOR=#FF0000]take note of your settings[/COLOR] (on a piece of paper), and click the radio button for 'no paging file' -->'Set', 'Apply', 'Okay'.
Then restart your computer and now you can run defrag as many times as you need to, without the big green block in the way.
   (*If you do this, don't forget to go back and turn it on again later, after the resizing is over, and Ubuntu is installed*).

If you will be using the Ubuntu 'Desktop' Live CD you will be using Gnome Partition Editor, a version of GParted, to do your partitioning. GParted can resize a FAT32 or NTFS partition regardless of whether it has been defragged or not. You probably don't really need to defrag first.

If you are using the Ubuntu 'Alternate' CD, yo will be using Partman disc partitioner, which does require the defragging of Windows first, or it will refuse to do anything.

It's generally a good idea to defrag Windows anyway though, Windows always works a lot better after defgragging.

Regards, Herman :)

---

### Post by imran7567 on 2007-07-13
I did what you guys recommended and it worked great. Here are the results. I am sure I can get better but compared to the one on top I am sure I can shrink this drive. 

[[IMG]http://img409.imageshack.us/img409/4719/defrag2jc6.th.jpg[/IMG]](http://img409.imageshack.us/my.php?image=defrag2jc6.jpg)

---

### Post by mikewhatever on 2007-07-13
Nice, you should have no problems resizing that.

---

