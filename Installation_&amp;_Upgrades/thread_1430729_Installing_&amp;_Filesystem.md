---
title: "Installing &amp; Filesystem"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by yester64 on 2010-03-15
Hi,

i just wonder what the best way is to structure an installation right.
Is ext4 good for everything or is it better to use different filesystems for certain folder.
The reason i am asking is that i read once that var would go better with a different filesystem.
Or, is there a guide which i can use to structure it right.

Right now i have everything on one partition, but with the next update i want to reorganize it better.
Any help is appreciate it. :)

---

### Post by yester64 on 2010-03-16
no one has a suggestion? wow... perhaps the wrong site.

---

### Post by Herman on 2010-03-16
:D Do you know how to use benchmarking software so you can tell the difference whether dividing up your installation into a lot of little partititons with various file systems in each one will actually be an improvement?

I have already started working on this exact same question in another thread.
To try to tell the difference I have two identical USB flash memory sticks, both with LUKS encrypted LVM installations in them. One has just a standard one-piece (or 'integral') partition scheme and the other is divided up into multiple partitions, with three of them being reiserfs, the other three ext4.

I wouldn't recommend anyone make rigid partitions because for sure sooner or later one partitions or another will get filled up and then it will be necessary either learn to live with a sub-optimal system or resize some of the partitions. For that reason I suggest LVM if you really want to make things that complicated for yourself.

I haven't had time to run benchmarking software yet. 
It's not easy for a human being to tell if there's any real performance improvement, but so far  the multiple partitions version is a little slower to boot up. It's possibly just a little quicker for some file operations but it's hard to tell. If there is any difference it would be negligible to the average user.

Unless you're fairly certain there will be a performance advantage to be gained from going to a lot of extra work and making things a lot more complex than they need to be, just stick with the standard one piece install.

More complicated does not equal better, it's just more complicated. 
Simplicity is bliss. :D

---

### Post by srs5694 on 2010-03-16
Judging by posts here, most Ubuntu beginners just create one big partition for Ubuntu (plus a much smaller one for swap) and forget about it. This seems to work fine for most of them. This runs counter to the traditional Unix way of doing things, though, which is to set up multiple partitions for a variety of reasons. Speed is only one of those reasons. I wrote a piece for IBM developerWorks on this issue a while back, so rather than take hours to write a complete reply, I'll just [refer you to it.](http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html)

The volume that a beginner is most likely to benefit from splitting off into its own partition is /home, which is where users' files are stored. Splitting off /home can simplify system upgrades, since you can completely wipe out your main installation without damaging your personal files.

---

### Post by yester64 on 2010-03-17
> **srs5694 said:**
> Judging by posts here, most Ubuntu beginners just create one big partition for Ubuntu (plus a much smaller one for swap) and forget about it. This seems to work fine for most of them. This runs counter to the traditional Unix way of doing things, though, which is to set up multiple partitions for a variety of reasons. Speed is only one of those reasons. I wrote a piece for IBM developerWorks on this issue a while back, so rather than take hours to write a complete reply, I'll just [refer you to it.]("http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html")

The volume that a beginner is most likely to benefit from splitting off into its own partition is /home, which is where users' files are stored. Splitting off /home can simplify system upgrades, since you can completely wipe out your main installation without damaging your personal files.

I like to thank both of you for replying.
A link is suffice to me and i am gladly reading through it. It can get confusing, i believe that, but for some reason i think it makes sense to split it in seperate partitions as with your example '/home'.
Since i want to make a complete new install i want to do it right and a little more advanced, as far as i can to my ability. :)

---

### Post by Herman on 2010-03-17
[Hard Drive Encryption in My Ubuntu Installation]("http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html") - Martti Kuparinen

The biggest problem for most people who decide to divide up their installations into many partitions is that a bad decision on partition sizes at installation time means they will need to resize partitions at some future time.
Linux partitions are easy to resize from the end of the partition, but the start of the file system is not so easy to move.
Fortunately, there's LVM, which means you can have as many partitions, (or volumes) as you like and resize them easily.

The link above shows how to use the Ubuntu 'Alternate' installation CD to install with LVM, you can disregard the encyption part of it if you like, it's up to you. Encryption adds security but it seems to slow down performance a little and it also makes things just a little more complicated when you need to fix something in your system from a LiveCD. 
With a little imagination you should be able to see how you can use the methods shown in that linked web page to your own ideas about how many partitions you'd like to have and for which directories.

---

### Post by Herman on 2010-03-18
:D srs5694
I have been reading your article,  '[Setting up UNIX file systems]("http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html")' - IBM and I think it's very well written.
Rather than supplying the answers it leaves me with quite a few important questions though. 

When a user wants to install an operating system with a view to achieving maximum performance, (speed), which file systems would you recommend for   /     /boot  /home  /usr  / var and /tmp and why?
 How should each of those file systems be mounted, (mount options in /etc/fstab)?

What size is considered a 'small' file?
What size must a file be before it is considered a 'large' file?

What file systems are more efficient at reading large files?
Which file systems are best used for writing large files?

What file systems are more efficient at reading small files?
 Which file systems are best used for writing small files?

When considering an installation where disk space will be limited, which file system has the least overhead?

When should file system journalling not be used? 

How much improvement in speed can a user expect to be able to achieve by creating separate volumes for   /    /boot  /home  /usr  / var and /tmp ?
Will it be worth the extra effort at installation time and the learning curve when something goes wrong and it's time to repair something?

Also, before a user will be able to begin dividing up their system into different partitions for each directory at installation time, they will need to know how much space to allocate for each partition. Any help?

Solid State Disks are improving in quality and reliability and prices are starting to become within reach of the average computer owner.
Some computer owners might be able to afford only a small SSD drive.  Maybe they also have a new hard disk and possibly an old hard disk lying around that can be also be used for part of an installation. Which file systems would you say should go in the SSD and which would be okay in each of the hard disks for best performance?

EDIT: Hmm, I found these pages where you have done a nice job of explaining a few things,

[Introduction to Linux filesystems and files]("http://www.linux.com/archive/feature/31939") -

[Optimizing Linux filesystems]("http://www.linux.com/archive/articles/31966") - 

 ... reading ... reading ... :-k thinking ...

---

