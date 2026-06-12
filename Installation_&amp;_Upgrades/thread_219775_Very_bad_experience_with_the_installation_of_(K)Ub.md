---
title: "Very bad experience with the installation of (K)Ubuntu"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by paracinac on 2006-07-20
Hello.

When I tried to install Ubuntu on the hard disk where I have prepared unformatted space of approximately 6GB I left with whole hdd reformatted. During the install (6 step wizard from the liveCD) I picked the option to automatically use the biggest continuous free space and my hard disk have been wiped out completely (I have lost the whole windows based installation on it wit big amount of data). ](*,)

When I tried to install Kubuntu the partitioner from the  installer (6 step wizard from the liveCD) did not let me to partition the hard disk as I want to. I would create 2 partitions (swap and ext3) of the appropriate size and format and then press the commit or next button and only one of the partitions would be formated...
After this problem, I've had a problem with wrong data displayed. I created a partition (aprox 1GB) and the partitioner tells it is 8 MB...

Really interesting.

Well this was a report (some kind of log) of two happy days and nights of swearing and cursing (and data recovering)... :), but I have one question to ask. I already spent several hours here on forum and other places on internet in search for the answer, but with no luck.
I want ubuntu and kubuntu in the same installation.
I try the:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install (k)ubuntu-desktop
but I just get the information that (k)ubuntu-desktop package does not exist. :-k 
I have a dial-up connection so the online repositories are just a dream for me. All I have is the (k)ubuntu cds shipped for free. I do not have the access to other type of discs either (additional and similar discs).

Is this doable anyway?

Thank you in advance.

---

### Post by zhoux on 2006-07-20
i assume that you can pick the Kubuntu CD as source for installing kubuntu-desktop...

---

### Post by Lord Illidan on 2006-07-20
sudo aptitude install kubuntu-desktop should work.. Or else.. sudo apt-get install kubuntu-desktop

---

### Post by paracinac on 2006-07-21
I probably haven't been clear enough in the previous post. :)
There are two scenarios and in those both I came to the same problem.

First scenario:
I use liveCD (from the shipit service) of Ubuntu 6.06 and I install it on my computer. Then I add the Kubuntu CD to the repository (in every possible way: apt-cdrom, synaptic, aptitude). I type in the console sudo aptitude (or apt-get) update and then sudo aptitude (or apt-get) install kubuntu-desktop. Then I get the message that kubuntu-desktop package does not exist.
When I add the kubuntu cd to the repository through the synaptic and do the reload from the package repository (I click on the appropriate the menu item to reflect the changes because new packages should be added to the repository) I do not get ANY new package.


Second scenario:
The same as the one above with one difference that I have installed Kubuntu and tried to add the Ubuntu.


Does anyone have a clue?

---

