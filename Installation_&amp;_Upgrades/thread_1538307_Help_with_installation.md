---
title: "Help with installation"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by Eagle-Six on 2010-07-24
I am a newb with linux but want to dual boot my laptop with vista and ubuntu. If I try to partition the c drive when installing it says that I have no operating systems and I have to partition the whole c drive. If I try to install alongside windows in windows, when it restarts in Ubuntu during setup it says no root or boot directory and wont go any farther. Any help wopuld be grateful. Thanks!!

---

### Post by Goolie on 2010-07-24
> **Eagle-Six said:**
> I am a newb with linux but want to dual boot my laptop with vista and ubuntu. If I try to partition the c drive when installing it says that I have no operating systems and I have to partition the whole c drive. If I try to install alongside windows in windows, when it restarts in Ubuntu during setup it says no root or boot directory and wont go any farther. Any help wopuld be grateful. Thanks!!


Before you install Ubuntu, have you backed-up / defragged your windows partition?  

Also, you could try partitioning the drive from outside the installer, i.e. in Windows, and try booting and installing to that newly created partition.

---

### Post by Eagle-Six on 2010-07-24
I did.  I even used acronis disk director suite to partition am 80 gb area for the install.  I burned the ISO to disc, tried to boot to install.  But when installation starts after I choose time zone i ckicked manually choose partition but it says I have no operating system installed like its a complete empty hard drive.

---

### Post by Goolie on 2010-07-24
> **Eagle-Six said:**
> I did.  I even used acronis disk director suite to partition am 80 gb area for the install.  I burned the ISO to disc, tried to boot to install.  But when installation starts after I choose time zone i ckicked manually choose partition but it says I have no operating system installed like its a complete empty hard drive.


So you're seeing only ONE possible place to install Ubuntu?  There isn't any other options as to where to install the OS?

Because if you already partitioned the drive that partition would essentially be 'blank' and OS free. . .

---

### Post by Eagle-Six on 2010-07-24
I have my c partition like 250 gb then backup partition then g drive that I partitioned for Ubunto for 80 gb or so.  but it just shows my whole hd for 3 hundred and something gb to be partitioned

---

### Post by kajankow on 2010-07-24
Take some pictures for them to help.

---

### Post by Goolie on 2010-07-24
> **kajankow said:**
> Take some pictures for them to help.

Screenshots would help,

I was googling around and saw a few posts that say sometimes partioning a drive *before* Ubuntu installation can cause you to have some problems.  Apparently, it would seem that preparing your partitions at the time of installing Ubuntu would be preferred.

All inferred from what my search resulted in.

Try, removing the partition from inside Windows and having Windows take the entire partition.  From there, boot into the Ubuntu screen and see if you can 'guided partition' the drive and shrink windows.

Remember to defrag / back-up your windows partition before doing so though.  Always better safe than sorry.

The G drive is a seperate hard drive or the partition you *created*?

---

### Post by Eagle-Six on 2010-07-24
that is the partition i created.  I only created the partition after i tried to install ubuntu the first time.  I am really new to all this.  I tried to boot from cd to install ubuntu and it said the same thing.  so then i went in to create the partition.  I cant through the installer because it said it would format my entire hd.  [IMG]http://www.ubuntu.com/sites/default/files/active/03_global/09_instructions/install_04_medium.jpg[/IMG]
This is the screen i get stuck at.  I got this pic on the homepage its not mine but maybe help.  on the top bar where it says this computer has several operating systems on it it say my computer has no os on it.  My vista does not show.  so if i partition to install ubuntu itll formaat all.  none of my partitions show up.

---

### Post by Goolie on 2010-07-25
I wish someone with a little more know-how could help us out.

My reco, try deleting the partition (drive G) inside Windows, defrag / back-up, and boot into the CD once more.  The option for guided partition should pop up.

Which install CD are you using?  I installed using 8.04, whatever number you are using, try one up or one down, maybe you'll have some luck.

But hopefully after you delete that partition and boot up you should get an option for a 'guided partition' and it'll recognize your Vista installation.

Good luck.

---

