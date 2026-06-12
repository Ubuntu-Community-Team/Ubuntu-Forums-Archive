---
title: "How to dual boot W7 and Ubuntu using raid 1 on both?"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by acatak on 2010-10-19
So, I searched the forum and I searched the web, but i still cant get a answer to how to do it without using fakeraid:

I originally used to run ubuntu under wubi through windows on my windows 7 fake raid 1using 2x500Gb hard drives.

I became better at ubuntu, and since Jan '10, I uninstalled windows 7, and ran ubuntu under softraid, with windows 7 in virtual box.

With the new school year, i need to use software like master cam and solid edge which doesnt work well in virtual box, nor wine.  

1)With the new release, I am looking to now dual both windows 7 and ubuntu using raid 1 with ONLY two hard drives.  Is this possible?  I have the option of fakeraid on my motherboard, but I would rather not go there.

Another option is to install Ubuntu using softraid with like 400 GB of the raid array, then install windows on one of the two hards drives, with what ever is less.  Since all my important data would be using linux, i could backup the small solidedge/mastercam files using usb.

Are any of the two options possible? Also (I have a quad core, and 4gb ram) would 64 bit or 32 bit be better(i would prefer 64 for windows)?


Thanks in advance!

---

### Post by acatak on 2010-10-19
condensed to one line:

How can I dual boot Windows 7 and Ubuntu using softraid (or fakeraid for windows 7) (raid 1) on both with 2 hard drives ?


Edit: reworded to make more sense

---

### Post by uRock on 2010-10-19
Moved & bumped.:)

---

### Post by ronparent on 2010-10-19
Short answer - if you want both in a raid on two drives, there is no way simpler than using fakeraid.

Windows simply has only the fakeraid as a software raid and can't be run from a linux software raid. An Ubuntu 10.10 install to fakeraid is relatively simple but should not be undertaken without some understanding of what a raid install looks like or behaves.

As a starter, some simple rules have to be followed:

1) Install Win 7 first
2) If Win 7 occupies the whole raid drive, use Win 7 disk manager to shrink it to make room for Ubuntu.
3) Use gparted on a live cd to place all your unallocated space for installing Ubuntu into an extended partition. This will insure that you will not likely exceed the 4 primary partition limit and thus bar an Ubuntu install.

Once prepared as above you should be able to install Ubunto to the largest unallocated space, as long as the partitioner recognizes the raid (ie the win 7 partitions will show in gparted). You should plan to run the install from the live cd so that you have determined beforehand that 10.10 will run on your system. Although there is a fakeraid howto for installing to a raid it won't apply to 10.10 nor should you need it. If you decide to go this route and run into problems, post here. Good luck.

---

### Post by protivakid on 2010-10-20
> **ronparent said:**
> Short answer - if you want both in a raid on two drives, there is no way simpler than using fakeraid.

Windows simply has only the fakeraid as a software raid and can't be run from a linux software raid. An Ubuntu 10.10 install to fakeraid is relatively simple but should not be undertaken without some understanding of what a raid install looks like or behaves.

As a starter, some simple rules have to be followed:

1) Install Win 7 first
2) If Win 7 occupies the whole raid drive, use Win 7 disk manager to shrink it to make room for Ubuntu.
3) Use gparted on a live cd to place all your unallocated space for installing Ubuntu into an extended partition. This will insure that you will not likely exceed the 4 primary partition limit and thus bar an Ubuntu install.

Once prepared as above you should be able to install Ubunto to the largest unallocated space, as long as the partitioner recognizes the raid (ie the win 7 partitions will show in gparted). You should plan to run the install from the live cd so that you have determined beforehand that 10.10 will run on your system. Although there is a fakeraid howto for installing to a raid it won't apply to 10.10 nor should you need it. If you decide to go this route and run into problems, post here. Good luck.

gparted does not see the fakeraid volume(s). Only the two discs themselves.

---

### Post by psusi on 2010-10-20
> **protivakid said:**
> gparted does not see the fakeraid volume(s). Only the two discs themselves.

Installing the kpartx package will fix that.

---

