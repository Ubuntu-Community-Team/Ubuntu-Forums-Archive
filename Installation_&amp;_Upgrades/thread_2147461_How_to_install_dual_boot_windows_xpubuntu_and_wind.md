---
title: "How to install dual boot windows xp/ubuntu and windows 7/ubuntu"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by pellyhawk on 2013-05-22
Hi everybody,

I'd like to install a dual boot windows xp/ubuntu and windows 7/ubuntu(I have 2 laptops, one is mine and the other is my employer's). How to install it?

Who can provide a web link for them? Many thanks.

---

### Post by ibjsb4 on 2013-05-22
You may want to read up on it first.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+xp&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+xp&sa=Search&cof=FORID:9)

---

### Post by Mark Phelps on 2013-05-22
For the laptop containing Win7, be sure to read through all of the material below BEFORE attempting the dual boot ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by Bucky Ball on 2013-05-22
[http://www.dogpile.com/info.dogpl.t8.1/search/web?fcoid=417&fcop=topnav&fpid=27&q=dual+boot+windows+xp+ubuntu&ql=](http://www.dogpile.com/info.dogpl.t8.1/search/web?fcoid=417&fcop=topnav&fpid=27&q=dual+boot+windows+xp+ubuntu&ql=)
[http://www.dogpile.com/info.dogpl.t8.1/search/web?fcoid=417&fcop=topnav&fpid=2&q=dual+boot+windows+7+ubuntu&ql=&timestamp=1369226769198](http://www.dogpile.com/info.dogpl.t8.1/search/web?fcoid=417&fcop=topnav&fpid=2&q=dual+boot+windows+7+ubuntu&ql=&timestamp=1369226769198)

There is just *so* much info out there about this. *Please* do some searching and researching before posting. Please check the first line of my signature. Then you will have some questions you want answered and we can help you with any brickwalls you come up against. Thanks. 

A tip from the forum's Code of Conduct (for everyone):

'Search for posts on the same topic before posting a new question. Sometimes using Google to search the forums works better than our own search function. You can do so by entering your search in the Google search bar followed by site:ubuntuforums.org.'

I suggest, before anything else, doing a search without 'site:ubuntuforums.org'. You often wind up here anyway. Here's another useful thread:

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Dated but still applies if you want the best chance of getting through the wall. Good luck.

---

