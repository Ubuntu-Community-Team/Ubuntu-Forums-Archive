---
title: "Error 17: Cannot mount selected partition"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by TeeAhr1 on 2007-06-26
Just reinstalled Kubuntu after some misadventures, and now when I try to boot I get "Error 17: Cannot mount selected partition."

In short, I am stumped.  Where do I go from here?

-pete

---

### Post by Herman on 2007-06-26
Hello TeeAhr1,
You should be able to boot up the Live CD and [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD"). That link should show you how to access your menu.lst and a couple of other vital files after you mount it too.

Now once you have the menu.lst file up, look at this, [     Grub error 17]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17"). and run sudo fdisk -lu or look with GParted and check if your operating system entry's 'root (hdx,y)' details are correct. Probably they are not, so you just need to edit that I think. Take a look and see if there is anything else obviously amiss before saving the file and closing. Reboot and spit out the CD and it should reboot okay.
That should fix it.

Or you could boot with [Super Grub Disk]("http://geocities.com/supergrubdisk/") and fix it from within Kubuntu itself.

Regards, Herman :D

---

