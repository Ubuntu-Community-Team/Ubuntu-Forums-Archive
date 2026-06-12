---
title: "installing ubuntu over windows partition"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by Kurisu87 on 2012-01-31
I have had a search but to no avail so here is my question, I am brand new to linux after being a heavy windows user. So im as noobie as you can get... 

I tried to install ubuntu but i got a little concerned when it stated it was going to wipe everything,  my current set up is 2 hdd one with just media which needs to remain, and the partitioned c: and d: drive 

C: contains the os abt 160gb and d: which contains document abt 70gb

What is would like is to overwrite the c: partition only keeping the d: partition and the media hdd un touched.  When I hit the install procedure it was quite confusing do I backed out and came here, so hopefully you can help this noobie in a crisis!

Thanks peeps

---

### Post by leonardodag on 2012-01-31
you can shrink one of the partitions to create another, which will allow you to choose which OS to load at startup, wipe one of the partitions and install ubuntu on the free space, or wipe the whole disk. For info on dual-booting windows and Ubuntu, see [this]("http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html").
Don't forget to make a backup.

---

### Post by dino99 on 2012-01-31
this is how i make install :

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Bucky Ball on 2012-01-31
Choose to manually partition when you get to that part of the install (the 'Specify Partitions Manually' option). Just kill the C: partition and install there. You would be advised to use these defaults and create three partitions:

/ = the OS, 15 - 20Gb plenty;
/home = your personal data, big as you like;
/swap = swap partition, 2Gb fine.

Other option is to 'Try Ubuntu' from the installation (Live) CD, open Gparted (partition editor), locate your C partition and kill it leaving free space.

Now when you get to the partitioning section during Ubuntu install there will be no confusion. Just create those three partitions in the free space (which should be the 160Gb where Win was). You will be able to access all existing partitions from Ubuntu.

Not sure what release you are installing but this one's for 10.04 LTS, a good place to start as most stable:

[http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)

This shows how to manual partition when you get to that bit under the heading '_Here's how you do a manual partitioning with /home:'_ Welcome and good luck. ;)

---

### Post by Kurisu87 on 2012-01-31
I will give those a try and report back I was looking in to using 10.11

And guys Thanks for all of the responses, one of the reasons for moving to linux was the community... Users helping users, no other systems community comes anywhere near the spirit I have seen while browsing through the forums

---

### Post by Bucky Ball on 2012-01-31
Welcome! But I think you mean 11.10 as there is no 10.11. But there is a 10.10. ;)

---

### Post by Kurisu87 on 2012-02-01
yea I went for 11.10 but have removed the sidebar unity??? and now have a Cairo Doc to replace it :)

---

