---
title: "reinstall and save separate encrypted home partition"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by John122 on 2010-04-26
It looks like I might have to do a clean install of Ubuntu. Something messed things up really bad and I have not been able to get any help on these forms. I have a separate encrypted home partition. When I reinstall Ubuntu will it automatically recover the encryption key for the home partition, or will I have to do some fancy maneuvers to get it to work? What options do I need to select during the install? Is there instructions some place I can follow? Thanks

---

### Post by ubunterooster on 2010-04-27
> **bodhi.zazen said:**
> I hear your frustration, but, what were you expecting ? That is the whole point of encryption. Encryption makes it one step more complex ...

The answer to your question depends on which tool you used to perform the encryption - LUKS or ecryptfs.

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

LUKS is a bit easier, in general see:

[How to: Resize an Encrypted Partition (LUKS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=4530641")

For any type of shared partition I prefer LUKS
LIkely is ecryptfs.

---

### Post by John122 on 2010-04-27
I have not tried any thing yet, but here is a few more links that might help if someone comes along looking for help on this subject. I suspect this is something a lot of people are going to be doing when the next version of ubuntu comes out later this month. Some of this are kind of out dated, but still my help.

[http://ubuntuforums.org/archive/index.php/t-1339370.html](http://ubuntuforums.org/archive/index.php/t-1339370.html)
[http://www.linuxquestions.org/questions/ubuntu-63/fresh-install-with-encrypted-home-partition-765465/](http://www.linuxquestions.org/questions/ubuntu-63/fresh-install-with-encrypted-home-partition-765465/)
[http://ubuntuforums.org/archive/index.php/t-1320687.html](http://ubuntuforums.org/archive/index.php/t-1320687.html)

---

### Post by Hansmc on 2010-05-11
I did some testing. I set up a clean install of Ubuntu 9.10 with a encrypted home in a separate partition. I put a few test files in home. Then installed Ubuntu 10.4 over the top of it. I selected the same partition for '/' and formated it. I selected the same partition as '/home' but did not format that one. I then used the same user name and password. The option for encrypting '/home' was already selected and grayed out so it could not be unselected. After install, home was readable and ready to go. I did not have to do anything else. 

There is lots of things that could make it so it would not work, so be sure to back up your files before you try it. Also note that I had home set up as a separate partition so if you did not manually set up your computer that way, this will not work. However, there may be some other way to do it.

Let us know if you have tried a something similar.

---

