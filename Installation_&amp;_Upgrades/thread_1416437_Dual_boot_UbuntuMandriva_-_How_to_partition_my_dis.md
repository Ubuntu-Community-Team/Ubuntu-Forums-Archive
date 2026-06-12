---
title: "Dual boot Ubuntu/Mandriva - How to partition my disk?"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by Tsabikos on 2010-02-26
First of all a warm hello to the Ubuntu community.
I recently made the move from windows to Linux and I am happy to having got rid off all the MS stuff. Trying out a few distros I decided on using Ubuntu and Mandriva (wife likes the flashier stuff, what can I say ;)).
 
  My question is how can I partition my hard disk in such a way that my /home is separate from both the Ubuntu and Mandriva part but accessed by both as my default home folder.

 I apologise if this might seem as a simple thing but I am an utter newbie to Linux, although willing to sink my teeth in it.

Thanks in advance.

---

### Post by ajgreeny on 2010-02-26
I would avoid having a single home folder as home for both distros as it may cause lots of configuration conflicts between the two.  Most of the configuration folders for installed applications are stored in home as hidden folders (starting with a . eg /home/username/.mozilla).

The simplest way to do what you want is to keep /home in the root partition of each distro, but only let the configuration folders sit there.  When installing the first distro, make a separate partition called "data" which you can then mount at boot time in each distro by editing /etc/fstab.  Now make sure every application saves its files, ie photos, documents, music, videos etc etc to that data partition, and make sure each distro user has read/write permissions to it, and you should be fine.

Comeback for more details if that all sounds like gobbledegook, and we'll try to assist more.  It may sound complicated to set up, but it's not really difficult, and once done it will make life very easy, and you will not notice the fact that data files are on a separate partition.

---

