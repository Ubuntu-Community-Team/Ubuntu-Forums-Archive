---
title: "Creating a home partition? mounting?"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by sent17inel on 2007-07-13
I know there have been a few threads about this and tutorials. But none for the exact situation im in. Im stil new to linux so step by step directions talored specifically to my situation would help.  I read psychocats tutorial on how to mount a home partition but i dont know how to do that. Currently i have created a partition of roughly 39 gig's and formated it to ext3. I have a 60 gig hard drive so the rest was just unformatted space which ubuntu just installed on. and now im running an upgrade. Where do i go from here? im still relatively new and confused. I read the tutorial and since its not talored to my current situation im lost completely. please help.....

---

### Post by merlinus on 2007-07-13
If you were unable to follow psychocats' tutorial on creating a separate /home partition after installing ubuntu, and since your install is new, you might just go to reinstalling.

That way, when you reach the partitioning screen, you can create three partitions: /, /home and /swap. You will also be able to specify the size for each.

Then /home will mount automatically, and things will work smoothly from there.

-merlin

---

### Post by Vajra Vrtti on 2007-07-13
> **merlinus said:**
> If you were unable to follow psychocats' tutorial on creating a separate /home partition after installing ubuntu, and since your install is new, you might just go to reinstalling.
I agree this is the easiest way. You have to chose manual partition during installation, but the dialogs are not difficult. Anyway, you can create and delete partitions, change your mind, do things again. Only at the end the changes to the partitions are really commited to disk.
> Currently i have created a partition of roughly 39 gig's and formated it to ext3.
What is this partition used for?

---

### Post by Pumalite on 2007-07-13
A good scheme is:
7 to 10 GB for '/'
500 MB to 1 GB for /swap
The rest for /home

---

### Post by az on 2007-07-13
> **Pumalite said:**
> A good scheme is:
7 to 10 GB for '/'
500 MB to 1 GB for /swap
The rest for /home

A better scheme is to forget about putting /home on a separate partition and just use / for everything (as per the default).

---

### Post by Pumalite on 2007-07-13
I bow to a more experienced user.

---

### Post by 3pinner on 2007-07-13
> **az said:**
> A better scheme is to forget about putting /home on a separate partition and just use / for everything (as per the default).

Please forgive my ignorance, but I'm about to try installing myself.
Why is just one partition best?
How about upgrades? It would seem that upgrading to a newer version would be easier and safer if my data were seperate from where the OS lives? Or have I been living in a cave too long :)

---

### Post by Vajra Vrtti on 2007-07-14
What I do is to keep my personal data on a separate partition, not under /home, which I use only to store application settings. So, I do a standard single partition installation and keep my data isolated.

---

### Post by sent17inel on 2007-07-14
Regardless. what i wanted was a separate partition for /home. And i got it!!! thanks you guys formatting the hard drive worked perfectly and i followed your recommendations.

---

### Post by az on 2007-07-14
> **Pumalite said:**
> I bow to a more experienced user.

Well, postcount means nothing...  There is more than one way to skin a cat.  A separate home partition may be a good solution for some.

> **3pinner said:**
> Please forgive my ignorance, but I'm about to try installing myself.
Why is just one partition best?

There is less chance that one of your partitions fills up since all the folders share the same drive space.  It is a simpler installation.  

99.9 per cent of computer users don't have to install an OS to use a computer.  To tell people that they should create a home partition when they install is false and it complicates the installation process which is already a big enough hurdle.

Keeping your home drive settings between more than one install to another may not always work.  The best thing to do if you ever bork up your desktop is to create another user and log into that user's session - that way, if it was a configuration problem, you can troubleshoot it.  Creating a separate home partition was popular years ago, before there were a lot of desktop apps.  

As well, there are much easier and safer ways to back up your data.

> **3pinner said:**
> 
How about upgrades? It would seem that upgrading to a newer version would be easier and safer if my data were seperate from where the OS lives? Or have I been living in a cave too long :)

It's easy to dist-upgrade.  You don't need to reinstall to upgrade.  If you want to do a reinstall, then it's probably less hassle to back up your data the conventional way (burn a disk, put it on another hard drive...  Drive space is a lot cheaper that it used to be)  

If you want to safely back up your data, it should be on another device anyway.  If your hard disk dies, it will take all the partitions with it.  A separate home partition is not a proper backup.

---

### Post by Pumalite on 2007-07-14
Well, postcount means nothing..

Your count is hidden. And I still think that a /home partition is a good idea.

---

### Post by merlinus on 2007-07-14
From my personal experience, Pumalite, I completely agree!

When the ubuntu install on one of my machines went south for some unknown reason, and I had to reinstall, all of the configurations, settings, and preferences carried over, including bookmarks, email messages and mailboxes.

A good example of 

ymmv

:)

-merlin

---

### Post by Pumalite on 2007-07-14
Glad you agree. I have the same experience.

---

### Post by Herman on 2007-07-15
:popcorn: Well I don't think having a separate /home is any replacement for a proper backup to some other media. 
I was sure glad we had my wife's music and pictures and stuff all backed up to seperate media the day I decided to delete her old Dapper install and replace it with a new Feisty installation. There was a little dirt n her CD/DVD drive and I still didn't know what was wrong yet, all I knew was that things were not working quite as well as they should, when 'Bam!" She had a corrupted partiton table and her hard drive looked as bare and empty as the moon! No partitions were showing at all! :(

Things like that don't happen very often and I admit I should have cleaned that CD/DVD drive out sooner. But luckily we had all the files backed up to separate media so we didn't lose anything. :)

We both multi boot so we prefer to have one-piece installs so our hard drives don't get so messy with lots of little partitions all over the place. Multi-booting's great for us because if she has any problem she isn't sure about while I'm away she just reboots into the other Ubuntu install and keeps on doing whatever it is she wants, so we really like multi booting. 
What I was actually planning on doing was mounting her other old installation when I got the new install done and copying the files from her old /home/username directory into her new install. Then when I was ready I was going to delete her old Edgy install and replace that with a new Feisty one too. It only takes few few minutes to transfer all the files from an old /home to a new one, so we don't miss anything really by not having a separate /home in my opinion.. :)

I'm with az, I think single partition installs are best and if you do have a separate /home, you shouldn't use it as an excuse to postpone making proper backups. Unfortunately, human nature being what it is, I'm afraid a lot of people don't make backups often enough anyway. :)

Regards, Herman :)

---

### Post by Pumalite on 2007-07-15
I have 4 external drives where I keep all my stuff backed up, but for everyday use I still prefer to have separate /home partition. There are always those missing pieces.

---

### Post by Herman on 2007-07-15
:) Hey, good answer!  I agree. External hard drives are great for that! I have a few of them too. That's what I use a lot, I only make a DVD backup once in a while.  :)

I think that's a good thing to use an external drive for too, data and files. :)

Ubuntu is such a great operating system that luckily we don't have to actually use our backups very often, except for user error. Or reckless users like me. (He-He) :)
It's odd that we have hardly any discussions in this forum about the best ways to back up data and lots of questions about how to rescue and recover data. (Mainly Windows users).

I use crontab to back up my email and other evolution stuff by running a backup scirpt every day first thing in the morning. It just makes it quicker to find everything if I ever do need it. That's okay for me because I have lots of hard drive space and not too much email.

Call me slow, but something interesting I learned just a few days ago is that original copies our installed packages go to /var/cache/apt/archives, (as long as we don't do 'apt-get clean'), so we should be able to back those up and restore all those too. I read it here, [http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html](http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html)
I tried copying a package for a small application (cairo clock) to another computer and installing it, and that worked fine.

Can  any of you fellows foresee any big problems with backing up and restoring added software that way? 
Or will I have to find out for myself, by trial and error?  I'm fatally curious. Probably I'll install make another installation as a test install for fun and see what I can get away with.  :)
That's another good thing about the multi boot approach, I can have a destroyable install and take risks to learn stuff safely without risking my 'good' install. :)

Anyone help me with advice on that though? Can we move packages from one Feisty to another safely? 

Regards, Herman :)

---

