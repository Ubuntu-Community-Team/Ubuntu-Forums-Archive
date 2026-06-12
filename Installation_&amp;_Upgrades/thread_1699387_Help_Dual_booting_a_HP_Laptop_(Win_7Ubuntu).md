---
title: "Help Dual booting a HP Laptop (Win 7/Ubuntu)"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by MrStephenson on 2011-03-03
Hello everyone, 
  One of my students would like to dual boot their windows 7 laptop with Ubuntu, I'd appreciate any advice you could offer.

Thanks, 

Mr Stephenson

---

### Post by BHEJU on 2011-03-03
There are lots of "How To"s on this topic on the web. You can pick the one which suites you. Here are few pointers to consider to make things go easy. 
-finalize your HD partitiong design first. (This depends a lot on HD size)
  meaning win os partition 25-30 gb (NTFS)
  Ubuntu OS "/" (and "/home" combined) 25-30 gb (EXT4)
  remaining space for data (NTFS or EXT)
-Install win 7 first (this is very import to make life easy) or you will have to edit boot sequences manually and that is risky.
-Install ubuntu second.

-I would make the data partion NTFS so that win7 and ubuntu both can read/write to it. (If you want to make this EXT partition then only ubuntu will be able to read/write to it unless you install third party app like EXT2FSD).

however, this is just for starters.. There are lots of options which depend on your needs and hardware configurations. I suggest you read couple of How-Tos to get better idea.
We are here if you have any specific questions.

Cheers,

---

### Post by oldfred on 2011-03-03
Some links to installs with graphical examples. If you have win7 installed use it to shrink the windows partition. Then use gparted to create new partitions for a shared NTFS and Linux partitions.

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
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

