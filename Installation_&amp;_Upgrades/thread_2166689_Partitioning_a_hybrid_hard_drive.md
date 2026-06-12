---
title: "Partitioning a hybrid hard drive"
date: 2013-08-10
forum: Installation &amp; Upgrades
---

### Post by GQDQALC on 2013-08-10
Hi guys. This question might have been asked here before but unfortunately I didn't understand any of the search results :( I'm rather new at this, sorry. 

I'm getting a Lenovo laptop with a hybrid ssd+hdd drive. My goal is to partition the drive for a dual boot of Win8 and Ubuntu such that both OS's have some of each. I want Ubuntu to boot from the SSD for sure, but since I only have 16 gigs of space on the SSD I want most non-essential data to be stored on the HDD. I haven't decided whether I want to boot windows from the HDD or the SSD yet; it might be faster from the SSD but it will also take up more of the precious SSD spaces. I definitely want to store data from Windows in the HDD (so most likely 50-50 linux and windows). The rest of the space can be used for caching or some such.

My question is, how would I accomplish this?

Thanks. PS: A beginner's explanation would be appreciated; I've been using Ubuntu for a while but I've never actually done this before. Thanks again! :)

---

### Post by russ2 on 2013-08-11
Well I am not sure if you understand what a hybrid drive is and how it works.  You cannot partition the ssd portion of the drive.  The ssd is used as a faster interface to the motherboard and all of your data is stored on the hdd.

---

### Post by oldfred on 2013-08-11
Usually with Windows 8 it uses Intel SRT and system is trademarked an Ultrabook. Since mostly Intel then the issues are similar for all vendors.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

 


You have to remove the RAID meta-data on both drives and then you can install Ubuntu into the SSD. See link in my signature for more info and other Ultrabook issues.

---

### Post by GQDQALC on 2013-08-20
Thanks for the advice guys. After further consideration and reading the replies I decided just to go all the way, 100% SSD. Then the partition becomes a snap and it's much faster. Have a great day!

---

