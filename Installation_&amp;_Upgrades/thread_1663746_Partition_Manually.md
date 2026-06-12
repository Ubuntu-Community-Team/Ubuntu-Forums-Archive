---
title: "Partition Manually"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by BanMidou on 2011-01-10
Hi

I`m a new  user to Linux.

I have ubuntu 10.10


their are 2 option during partition one is automatic other is manual.

I have windows Vista SP2 business
My computer configuration is a 320GB HD
core 2 Duo 2.80Ghz
2 GB Ram.



i have partitioned windows such as C D& E

I have nearly 172 Gb or in other words my E drive is free.
:D

Well to me the as I`m a first time user ubuntu is a bit confusing

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I have referred this link but 

how Do I know what is dev sda 1 etc how do i make sure ubuntu gets installed on D rive and not in My windows C drive


Can anyone guide me and suggest me a link or perhaps a book related to linux with which I can learn more.


Is an antivirus required for Linux??

I saw a page in wiki but these are quite old threats is it possible that linux has changed to such an extent that its immune.

Is virtual BOx(have used) and wine the same.

Is Pidgin a safe OpenS program for Linux

I`m planning to install vlc too.


I know its lame to ask but by chance is MS OFFice gonna become available for linux

I have used open office but was disappointed a bit.

are their more alternatives.

will be happy if someone suggests a Video conveter tool as well

thanks in Advance

---

### Post by garryconn on 2011-01-10
> Can anyone guide me and suggest me a link or perhaps a book related to linux with which I can learn more.


[LIST]
[*][http://www.linux.org/lessons/]("http://www.linux.org/lessons/")
[*][https://help.ubuntu.com/10.10/newtoubuntu/C/index.html]("https://help.ubuntu.com/10.10/newtoubuntu/C/index.html")
[/LIST]

> Is an antivirus required for Linux??


Google can be a great friend... check out these pages that offering advice, opinions, and suggestions about that:

[LIST]
[*][http://www.google.com/search?q=Is+an+antivirus+required+for+Linux]("http://www.google.com/search?q=Is+an+antivirus+required+for+Linux")
[/LIST]


> I have used open office but was disappointed a bit.


Why? It disappoints me to pay onwards of $1000 for something that I can get for free. What are the things that disappoint you with Open Office. What ever trouble you're having, I am sure there is a solution.

---

### Post by BanMidou on 2011-01-10
Hi thanks mate for   a quick response.


But the links you gave me don`t really explain about partitioning the Drive

I still can`t understand whether devsda 2 or dev sda 3 stand for E or D drive according to windows.


Can someone Guide me please

Cause each time I use automatic it goes installs itself in my 
C drive  
How do i make sure that linux gets installed on a drive with

100GB :confused:

I`m stuck like this now for nearly 4 hours :confused:


Please help Please Help

---

### Post by dino99 on 2011-01-10
here is what you need:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

your actual "drive E" can be prepared (as said into the above link) to install ubuntu

---

### Post by kansasnoob on 2011-01-10
Regarding installation check out these three links:

[http://ubuntuforums.org/showpost.php?p=10119443&postcount=1](http://ubuntuforums.org/showpost.php?p=10119443&postcount=1)

[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

There is a very real bug in the "Install alongside" option in the 10.10 live installer:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

So after looking at those links if you need more personalized help please use the Live CD to post the output of the following command:

```
sudo parted -l
```

BTW that's a lower case L.

---

### Post by BanMidou on 2011-01-13
thanks a ton guys am gonna Try what you said 
@ kansasnoob
 dino99

Thanks Mate :)

---

