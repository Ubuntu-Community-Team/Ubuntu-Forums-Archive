---
title: "doubt about File system"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by srinath on 2005-09-07
I have two disks. One is 20GB and the other 40GB. I was planning to give ubuntu 10GB and windows 10GB. So, 10GB is going to be under the ext3 file system and another under FAT32. What about the 40GB disk? Which file system should it be in? I want to use it for storing audio and video and misc files that I will use under windows or Linux.

---

### Post by Stormy Eyes on 2005-09-07
If you need to access the 40GB drive under both Windows and Linux, then make it a FAT32 drive.

---

### Post by srinath on 2005-09-07
Thanks.
Can I do this - Use the 20GB for Linux and the 40GB under FAT32 and install windows in it?
Just snooping around for options.

---

### Post by d1337 on 2005-09-07
Yes, you can.  The [Unofficial Guide](http://www.ubuntuguide.org) has instructions on mounting FAT and allowing read/write capabilities.  If you haven't installed either yet, now is the best time to make an educated decision.  You could still give Ubuntu 10G, MS 10G, and format the remaining 40G as FAT for the express purpose of using to store audio/video files which would be accessible by either OS.

d1337

Read another post that seems to indicate that some folks have issues mounting FAT partitions larger than 32G.  While I have been able to mount my 40G windows partition, this may not work for you.  Either way, insure that you can successfully mount the FAT partition from either OS before relying on it...otherwise could be a time consuming frustartion.

---

### Post by srinath on 2005-09-08
Well, I am not planning to keep the 40GB as a whole! I will split into into 10s or 20s maybe!

But I will go through the Guide as you suggested.

hmm... did everyone feel a little lost while trying to use the resuce disk thing while trying to format the drives into EXT3 and FAT32? ??:

---

