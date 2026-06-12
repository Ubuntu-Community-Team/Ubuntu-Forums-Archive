---
title: "Win 7, Ubu &amp; 5 partitions"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by Witch Lady on 2011-02-25
Hello, I know that there were already some topics about Win 7 & Ubu on 1 disk. But I didn't find all the information I want, so I want to ask experts here. I'm a newbie when it comes to Linux. 

I'll be buying 1TB hdd soon and I will install Windows 7 & Ubuntu on 1 disk. I've read somewhere that there should be only 4 partitions. But I need 5: 1 for win, 1 for ubu, 1 for my documents, 1 for my games and 1 for videos. Do I need a swap partition as well? Can I install it like that? (Quad 2,4GHz 4GB RAM). 

Also, any suggestions on which Ubuntu should I install? 10.04 or 10.10. 32 or 64bit? My processor is capable of handling 64bit, but I wonder if it will be ok with the drivers and soft. 

Thanks in advance for help.

Witch Lady.

---

### Post by oldfred on 2011-02-27
Windows has to be in a primary partition and you can only have 4 primary partitions. But one primary partition can be an extended partition which can hold many logical partitions. Windows will read data from a NTFS partition that is logical and all of Ubuntu can be logical partitions. Do not try to create more than four partitions with any windows tools as that will convert to sfs or logical partitions that are not compatible with anything (even windows has some issues ).

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Installs -----------------------
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)


GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

