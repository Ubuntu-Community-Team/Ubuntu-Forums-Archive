---
title: "How to Upgrade from Pop 76 to Ubuntu 18.04"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2018-04-27
I have created an Ubuntu 18.04 install USB which I want to use to replace the Pop! 76 OS which came on my laptop.  But I am not given the option to upgrade, only to install beside Pop! 76 or to erase the disk which will require me to backup and then restore 160GB of data, which from experience when I first restored that data to the laptop will take a day or two.

How do I update in place.  I want all of my computers to be running the same OS.

---

### Post by QIII on 2018-04-27
Hello!

Although based on Ubuntu, Pop!_OS is not Ubuntu.  So you can't "upgrade" to 18.04.

What you may be able to do (after backing up your important files) is install Ubuntu while maintaining your /home directory (if System 76 does their installations with a separate /home directory).  Even at that, there is a risk that Pop!_OS installs some user config files in /home that will result in a borked system.

Best option may be to bite the bullet anddo a good backup to external media  and install Ubuntu using the whole drive.

You should ALWAYS backup before an upgrade or reinstallation anyway.

---

### Post by 7-webmaster on 2018-04-27
How can I backup 160GB of data?  The last time I did this I did it across my home wi-fi network and it took TWO DAYS!

---

### Post by willfoot on 2018-04-27
Not sure if this was meant rhetorically. In case not: with an external hard drive. How are you backing up day to day, when not upgrading your OS? A 5400 1TB drive shouldn't break the bank.

---

### Post by 7-webmaster on 2018-05-01
So I went out, bought an external HD, backed up my home directory, installed Ubuntu 18.04, restored the home directory and now EVERYTHING is broken because every product I have tried ignores the restored information.  And most of the products I was using are not part of the Ubuntu 18.04 package so I have to individually re-install all those products that I already had installed and configured.  I have been working at that for a day and still most of my system is an expensive door-stop!  All because the Ubuntu 18.04 installer doesn't support upgrading an existing system.

---

### Post by QIII on 2018-05-01
It supports upgrading an Ubuntu system.  But, again, Pop!_OS is ***not*** Ubuntu.

Did you restore your data only, or did your do a wholesale restore of your /home?  As I said above, if Pop!_OS uses user config files differently -- and you just restored your /home directory whole cloth -- that might cause problems.  If the packages they use are slightly different, you may have problems.  It should not be surprising that one would have to reinstall software from a different set of repos.

---

