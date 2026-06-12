---
title: "A partitioning question"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by Scarcer on 2010-11-04
Okay, I'm reinstalling Ubuntu since .04 failed to upgrade to .10, aside from another mess I created.

Simple fact aside, I'm attempting to do my partitioning a little different this time.

Was thinking of doing something like this.

/ <--- base partition which I want to mount all operating systems on individually

/ubuntu <--- ubuntu os files here

/linux2

/linux3

/storage

etc etc, you get the point.

So instead of os files being on /, I desire them to be in designated partitions.

Exactly how do I go about telling the installer to install in /ubuntu and not /

I'm guessing its the 'make primary' option?

Does that designate that partition as the OS's primary partition, or does that make it the primary for the entire HD?

Would it be safe to put the boot loader in /?

---

### Post by oldfred on 2010-11-04
I do not understand. / (root) is where everything is installed, you cannot have multiple systems in root. You could install different desktops, but I am not sure I even recommend that.

I have three / partitions, old install, current install and (future) install. I mount my /data into each and usually copy some or most of /home from old to new. Since I aggressively move data & hidden data folders out of /home it only has user settings.

Primary is just a type of partition. Ubuntu installs the same to primary or logical partitions. If you are planning on windows you need to reserve primary partitions as the first copy of windows has to be on a primary to boot.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by Scarcer on 2010-11-04
okay, then I'm guessing that every installation mounts every partition individually. Mounts on one file system wont apply to another linux based os, right?

---

### Post by oldfred on 2010-11-05
You can share a data partition that you mount in each system. System partitions are not to be shared. If you are installing the same system you may be able to copy some data. Some have shared /home but that has risks where software is not compatible so files can get corrupted. If you create unique users you can share the /home partition but all files are separate so that defeats most of the purpose of sharing.

---

