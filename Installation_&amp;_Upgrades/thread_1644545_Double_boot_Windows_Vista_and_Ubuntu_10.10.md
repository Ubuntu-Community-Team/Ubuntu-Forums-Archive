---
title: "Double boot: Windows Vista and Ubuntu 10.10"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by pako el chako on 2010-12-13
I'm a newbie, not much to add to that. I've read on some sites that you must do a partition of disk. My HDD has at the moment only 2 partitions, C: and D:, which is recovery. I want to make three primary partitions: ntfs, another for /: and an extended one. In the extended I'd like to get 3 logical partitions: Swap, /home and a partition for shared data. I don't know which system of files I should use in the shared data partition, I've read that fat32 is good, but those posts were from 2005 =S
So, summarizing, I need you to tell me if my partition hierarchy is good, if so, tell me how to do it and if not, recommend me a better one. I need to know which system is better for /:, if ext3, ext4 or what. And I also need you to tell me how to make a shared files partition and which system of files I should use. =)

---

### Post by oldfred on 2010-12-13
Welcome to the forums.

Your plan is good. Note you only can have 3 primary partitions and the fourth is the extended that is a container for all the logical partitions.

I recommend NTFS now. About 4 years ago I used FAT for my shared partition, but I was putting some large files into it and did not know it had a limit of 4GB (Files were lost). It also does not have journalizing for repairs. You can use FAT for small devices like flash drives where you have to for cameras or others that have to have FAT.

My standard recommendation, Ubuntu's standard is now ext4.
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

I like to use gparted and partition in advance. The installer will not let you create the NTFS partitions as part of the install anyway (you would have to just leave space). Then when installing you choose manual install. You then select which partition is / (root) and its format, which is /home and its format. If you created swap in advance it will automatically find it. 

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by sikander3786 on 2010-12-13
Welcome to Ubuntu and also the forums :-)

This page would be helpful.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

You need to shrink your Windows partition and then create and extended partition in that freed up space. And then you can create as many logical partitions in that as you want to.

If you didn't know, you can place your '/' partition inside the extended one as well. Linux doesn't need a primary partition to boot from.

You need to format your '/' and /home partitions as either ext3 or ext4. I would prefer ext4 as that is the upgraded version of ext3 and is also the default FS for Ubuntu 10.10.

Shared data partition shoud be formatted NTFS as Linux now supports NTFS just like a native Filesystem. And NTFS is way better than Fat32.

Feel free to post back any queries. In fact, it would be easier to tell you when you ask something as we don't know how much you know about Linux and regarding what issues you need help :-)

---

### Post by pako el chako on 2010-12-13
Both answers seem quite useful, thank you very much! I'll try your advice and then tell you how it went.

---

### Post by Quackers on 2010-12-13
So long as you don't exceed the 4 primary partitions (or 3 primarys and one extended) on any one hard drive the possibilities are endless.

---

### Post by pako el chako on 2010-12-13
I have a doubt, if Linux can support now NTFS, is it really necessary that I create another partition for shared files, or will Ubuntu be able to read the aforementioned files automatically? If I do need to create a separate partition, how should I name it? And another doubt. What does "mounting partitions" mean?

---

### Post by oldfred on 2010-12-13
I still like a shared partition. I do not write into a different operating system from a foreign system as that can lead to issues. I do read from my Windows and only write into it if I have to make repairs from Linux. I just labeled & created a mount called "shared".

In Linux you have to have a place to mount a file system and then you mount a partition to that place.

Simple examle, you lose the mount on reboot.

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data

If you want to have it available everytime you reboot then you need to edit fstab.
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I prefer manual editing, as I have had issues with some of the graphical versions (I ended up editing the entry anyway).
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

---

### Post by presence1960 on 2010-12-13
> **oldfred said:**
> I still like a shared partition. I do not write into a different operating system from a foreign system as that can lead to issues. I do read from my Windows and only write into it if I have to make repairs from Linux. I just labeled & created a mount called "shared".



I agree with oldfred on that. I have a separate disk for my data that my OSs (Ubuntu, Sabayon & Win 7) can read/write. Never had a problem with that setup. A separate partition will do the same thing as a separate disk.

---

### Post by pako el chako on 2010-12-14
Nice links, but I'd like to know how to partition if my Windows Vista already took my whole HDD. How do I partition without erasing important data?

---

### Post by Quackers on 2010-12-14
Use Vista's disk management console to shrink the vista partition.
It is recommended to defrag Vista first, at least once, preferrably twice.

---

### Post by pako el chako on 2010-12-14
Thanks, I followed your advice, but even though I have about 50Gb of free space, diskmgmt only allowed me to reduce C:\ by 2Gb... =(

---

### Post by Quackers on 2010-12-14
That can happen sometimes.
Did you defrag?
Also it will sometimes allow much more shrinkage if you set the paging file to none. Google for that - I can't remember how, but it's quite simple :-)

---

### Post by pako el chako on 2010-12-14
Yep, I did defrag two times, but I'll Google the paging file and tell you how it went. =D

---

### Post by Quackers on 2010-12-14
Ok, good luck :-)
When you've finished resizing again, don't forget to turn the page file back on :-)

---

### Post by pako el chako on 2010-12-14
I hate my laptop ¬¬ Haha, I turned to none my paging file, but still can't get more space from C: >=(

---

### Post by Quackers on 2010-12-14
In that case you will need to use something like Gparted Live cd (not the one in Ubuntu) but this carries some risk. If you download the live cd file and burn to cd and then boot from it, it can resize your Vista partition much more than Vista will. I have never had a problem using it, but I have heard of others who have!
Your choice I'm afraid. It depends how desperate you are for free space.
I would certainly backup Vista first, possibly with a Clonezilla image, or similar.

---

### Post by pako el chako on 2010-12-14
Maybe I'm not meant to use Ubuntu, ever. I might get an external HDD, sounds safer. What do you think?

---

### Post by Quackers on 2010-12-14
It's a possibility! Have a think about things :-)

---

### Post by pako el chako on 2010-12-14
I guess this one's a solved one... Thanks a lot for the help, found it quite useful. Later!

---

### Post by pako el chako on 2010-12-14
Do you think a 160Gb iPod might work as an external HDD?

---

