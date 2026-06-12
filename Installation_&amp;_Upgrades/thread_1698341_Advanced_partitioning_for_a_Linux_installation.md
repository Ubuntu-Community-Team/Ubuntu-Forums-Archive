---
title: "Advanced partitioning for a Linux installation"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by swift100 on 2011-03-02
[SIZE=2]Hi, I've posted this on linuxquestions.org already but I'd like to receive more opinions from advanced linux users. It's basically a consideration about disc efficiency when it comes to the filesystem and dual HDD configs. Please say what you think :)[/SIZE]

[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]It seems more reasonable to have a simpler filesystem for normal desktop use. On the other hand the idea of the filesystem spread across +120GB is somewhat questionable to me... 

The concept of shortening seek time is worth considering, especially in dual HDD configurations. Having 2 spindles reading / writing the requested data at the same time would be definitely advantageous. I'm wondering how would this be achieved in linux?

NTFS by default tries to squeeze data as close to the start of a volume as possible thus creating fragmentation problems. Correct me if I'm wrong, but still, defragmented data should be better accessible with shorter seek time on an NTFS volume. From what I've read a linux filesystem will try to spread data evenly throughout the volume hence leaving a considerable amount of space for files to grow or be easily moved, preventing fragmentation. In this case if I have a defragmented 30GB NTFS partiton filled with 5GB of data the head will call whatever it needs from the beginning of the partition finding the placement of files in the MFT (also at the beginning of a volume). If this were linux wouldn't this data be spread throughout the whole partition? If so the head would need much more seek time to call files which are far from each other.

source: [http://geekblog.oneandoneis2.org/ind..._defragmenting]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

[I]"A linux file system scatters files all over the disc so there's plenty of free space if the file's size changes. It can also re-arrange files on-the-fly, since it has plenty of empty space to shuffle around. Defragging the first type of filesystem is a more intensive process and not really practical to run during normal use.
The cleverness of this approach is that the disk's stylus can sit in the middle, and most files, on average, will be fairly nearby."[/I]

The above article states that it's beneficial that linux spreads the files more or less "in the middle" so the head can retrieve them starting from the middle on average. What about if we have 100GB of space for this retrieval? Won't it be too far apart so to speak for efficient seeking? I imagine the head running across the whole 100GB chunk of the platter in a fairly random logic. I know that the information about the placement is located in something called a "superblock" but still it's a mistery for me how would scattering files across a large space be beneficial speedwise?

It's definitely a good idea to divide the system partition from programmes in Windows and put on separate disks,preferably at the front. Big gain from:
a) smaller load for the system partition 
b) 2 discs working simultaneously when calling files which reduces latency
c) utilising the outer zone which has best performance
d) easier maintenance of a divided filesystem 

Would there be a similar benefit from separating / and /usr (maybe some other) and putting on 2 different disks? Doing this the filesystem, data and programmes could be read independently to a certain extent increasing access times. I'm not taking into account some special needs resulting from e.g. a dedicated mail server or sth similar. HDD performance only in more or less "standard" operation. 

Regarding the swap partition when I tested the system by opening all apps I have (no VM ware though) it wasn't even close to the amount of ram and swap was on 0% usage. Maybe a file which I can modify in size is more beneficial unless someone uses vmware or video / sound processing a lot.

Long post [IMG]http://static.linuxquestions.org/questions/images/smilies/smile.gif[/IMG]

If anyone has some experience with spreading mount points over multiple discs please write.[IMG]http://static.linuxquestions.org/questions/images/smilies/smile.gif[/IMG][/FONT][/FONT][/COLOR]

---

### Post by mikewhatever on 2011-03-02
With most modern hdds, the average seek time is measured in milliseconds, so that defragmenting (special cases aside) or the other optimization you've mentioned become meaningless. I'd just use one hdd for Ubuntu and the other for data. 
PS: If you want speed, look into a RAID0 solution.

---

### Post by cchhrriiss121212 on 2011-03-02
Or just get an SSD for root, HDD for /home.

---

