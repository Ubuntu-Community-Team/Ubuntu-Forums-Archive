---
title: "Can I install packages to 2nd hard drive??"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by billwrtr on 2010-05-26
I have two SSDs: a 4 gig and a 16 gig. Being not terribly Ubuntu wise, I did a clean install of 10.04 to the 4 gig. Now it's almost full. I can easily save future data to the 16 gig drive, but what if I need to install additional packages. Is there a way to set up the system so that I can install software to the 16 gig more-or-less seamlessly?

The 16 gig drive is mounted in ./media. 

Many thanks in advance,
-Bill

---

### Post by WinRiddance on 2010-05-26
Why don't you back up the entire content of the 4 GB disk onto a physical hard drive with either rsync or better yet a program such as this one here: [Back in Time.]("http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html")
Here's some more info. on that: [http://backintime.le-web.org/download_page/](http://backintime.le-web.org/download_page/)

Once you've created an image of the entire 4 GB content you should be able to back up that saved image onto the 16 GB disk as long as they're both using the same file system. The 16 GB disk should then work just like the 4 GB one, with the added benefit of being able to install more apps etc.

---

### Post by srs5694 on 2010-05-26
Linux stores particular types of data in specific directories. For instance, most programs reside in /usr (and in particular subdirectories of /usr, such as /usr/bin for program binary files, /usr/share/man for manual pages, etc.). Thus, if a partition (such as root (/) or /usr) fills up, the only option is to move some or all of it to another partition. For instance, if everything is on root (/) right now, you could move /home or /usr to another partition, mounting that partition at the appropriate point. There are numerous online guides for doing this; try Googling "moving /home in Linux" or something similar. (I don't have recommendations for specific sites that cover this topic, I'm afraid.)

---

### Post by oldfred on 2010-05-27
I used this to move /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies
# see grub cleanup to remove old linux versions or use synaptic
# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

---

