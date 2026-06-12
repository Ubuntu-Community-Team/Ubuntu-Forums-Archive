---
title: "Installation hangs at partitioning"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by Stkh on 2005-11-03
Hi,

I'm trying to install Ubuntu 5.10 on a HP vectra PIII 866MHz box with two HDD, one with a Debian installation and one with an inactive Win2K installation. Installation proceeds nicely (default installation, Danish location) until it starts the partitioning program (proceeds to 100%), the it shows only the blue screen with the white line in the bottom, but without any content. I can press enter, then teh white line in the bottom expands upwards, or I can press Ctrl-C and enter, after which installatin proceeds to the next step, "starting up the partitioner", that proceeds until 52%. Then everything hangs.

Any suggestions are most welcome! I'm pretty new to Linux so please handle with care :-)

---

### Post by Stkh on 2005-11-03
I found the answer to my own question, thanks to Tom Marshs blog ([http://marshonsmacs.blogspot.com/2005_10_01_marshonsmacs_archive.html)](http://marshonsmacs.blogspot.com/2005_10_01_marshonsmacs_archive.html)). I needed to delete the partitions on the Debian installation  (using FDISK from an old Win98 box), then everything worked.

Cheers
Steen

---

### Post by bkorb on 2007-09-02
And if, for example, you want to _keep_ the data that are in the partitions, then what?  It seems that is the predicament I'm in, but I'm not sure.  I got here to a re-install because I got a new monitor and there do not seem to be normal human usable tools for updating that.  So, I tried xorgconfig.  X is gone.  But I have a lot of stuff I want to keep in my /home partition.

---

