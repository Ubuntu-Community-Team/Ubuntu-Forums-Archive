---
title: "Hard disk problem"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Santolman on 2011-03-04
Hi, First off, I'm new to this forum and to Ubuntu / Linux  :)
I first installed Ubuntu about a week ago, I love it but because I was a noob I decided to reinstall it because I messed some things up, But I've got a problem reinstalling it. I used a windows 7 32-bit dual boot +  Ubuntu 10.10 32 bit, the dual boot worked fine. After removing Ubuntu I removed the partitions also so I had 1 partition on my hard disk, after that I tried to reinstall Ubuntu, Tho I've got problems installing it. Where I could choose how much disk space I wanted to use on the previous install it now says Ubuntu wants to use the entire disk :
[IMG]http://i54.tinypic.com/vpusjn.png[/IMG] 
It is Dutch but I hope you get what it means.
It says It will delete 1 partition when I use this.


When manually Creating a partition I get this: 
[IMG]http://i56.tinypic.com/20f71mx.png[/IMG]
It says it can't see how much disk space I've already used, when  On windows it says I have about 70 Gb left, due to this I can't seem to install it. I've done a disk repair but no luck.. 

Then I used the liveCD to use Gparted and it showed me this:
[IMG]http://i51.tinypic.com/2m2feqb.png[/IMG]
I don't know how it comes up with 3.81 unallocated disc space, when I want to create a partition I can only go up to 4 mb... I've read the forums and tried searching but I can't seem to find my exact problem. Help is much appreciated. 

Ps. Sorry for my bad english, if you don't understand what I'm saying, please tell.

---

### Post by dabl on 2011-03-04
Do not use NTFS for a filesystem type on a Linux system.  Use ext4.

---

