---
title: "Hard disk requirements for Ubuntu Server install"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by cpedros on 2007-11-21
Based on the link below I spent some time clearing up the measly 20GB hard drive on my old XP laptop to free up roughly 4GB for a dual boot Ubuntu Server install. 

[http://doc.ubuntu.com/ubuntu/serverguide/C/preparing-to-install.html#system-requirements](http://doc.ubuntu.com/ubuntu/serverguide/C/preparing-to-install.html#system-requirements)

Given the details in the link say the server has a small profile and requires 500MB hard drive space I was surprised when I started the partition process from the Ubuntu CD I burnt that the install would require 9.7GB!

Is this correct. Details seem to be conflicting... or am I doing something wrong? Any help very much appreciated. 

Thanks

---

### Post by rmemm on 2007-11-21
I think 9.7GB seems large, but I am using the Dapper Ubuntu Server edition.

One would think the base system would fit on 2GB for Dapper.  One actual install I've done took about 1.5 GB.  In addition I have an 8 GB data partician in that case to hold my content -- but this is not related to the base size of the install, I also 512 MB swap partician -- and I used 512 MB of memory.

Personally I like about 8 GBs for any Ubuntu install because it's flexable -- gives you extra space to work with and is big enough even for the desktop install.  But as you said -- something like 4 GBs for the server should be OK if you don't have that much data.  At least for Dapper.

Rob

---

### Post by cpedros on 2007-11-22
Rob - thanks for the feedback and advice. However the actual install process, when I selected the guided resize of the master partition, is enforcing the 9.7GB minimum with out the ability to change it (Ubuntu 7.10 Server Version by the way). 

The statement is a long the lines of "install requires 9.7GB minimum and 11.7GB maximum". I can post a screen grab if necessary. Since I'm a complete noob to Ubuntu and partitioning my HD for dual boot I'm unsure if this is expected behaviour or if there is something I am doing wrong that is enforcing this, what I view to be, over generous HD space requirement for the install.

Cheers

---

### Post by rmemm on 2007-11-22
Sorry can't really help with 7.10 specifically, but it seems stange -- 10 GB -- that's huge.  I thought the whole idea of Ubuntu server is that it is kind of small.  

Other thing -- on Dapper at least -- there were several installs you could do -- by that I mean at least two.  I generally do the stripped install, then add in what I want manually using apt-get.  The number I quoted for you is striped but with LDAP, Apache, Plone, and a few other things added to make the real server.  

The other one is the LAMP distribution -- which is a common server configuration.  I don't use that because I want something a bit different myself.

By the way -- what sort of media are you installing from -- 700 MB CD or a 4GB DVD?  I ask -- because a 700 MB CD probably contains at most 1.4 GB of data if you take into account compression.  Don't see how the base install can be sooooo big.

Rob

---

