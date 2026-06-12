---
title: "Offline Repo without cd/dvd"
date: 2014-07-16
forum: Installation &amp; Upgrades
---

### Post by djheadley on 2014-07-16
I'm running Ubuntu 12.04 and just recently put together an older desktop computer as my other one died.  I need a way to update this "new" box with the packages from my laptop which is up-to-date.  The laptop doesn't have a cd/dvd burner and I don't have access to an external one.  I remember some time back where a repo could be set up manually, I've tried the programs set up for this but they require a burner.

I know the manual setup takes more time, etc. but I'm stuck otherwise.  BTW I have limited bandwith.

---

### Post by sudodus on 2014-07-16
It is possible to make your own mirror for the Ubuntu repos, and I have seen it described. I don't remember where, but you should be able to find it.

There are also another alternative.

Take advantage of the fact that Ubuntu is portable between computers as long as you have not installed any proprietary drivers. So you can update/upgrade and install packages in (or connected to) one computer, and then move you drive to another computer and it will run.

If both computers can boot from USB, this will be rather simple and straight-forward. Get an external enclosure or a 'USB to IDE and SATA cable' and connect the drive that way.

---

### Post by djheadley on 2014-07-21
I've done this (cd/dvd repo) in the past but I can't find where I got the info from.  I ended up just making sure the version numbers matched and download/install.  I hope I don't run into any problems.  I'm having to use 12.04 on both machines because 14.04 won't run on the desktop until I get more memory for it.  Thanks anyway.

---

### Post by sudodus on 2014-07-21
Try according to the following link (it appeared a couple of days after our posts in your thread, and might be a solution for you)

[http://ubuntuforums.org/showthread.php?t=2234850&p=13076109#post13076109](http://ubuntuforums.org/showthread.php?t=2234850&p=13076109#post13076109)

---

### Post by ian-weisser on 2014-07-22
Most offline machines don't generally need lots of updates. 
If you really *want* to update an offline machine, the basic theory is that:


1) Packages are stored in /var/cache/apt/archives and owned by root on all Ubuntu systems.
2) You can move packages between systems...unless the package depends on a different kernel architecture.
3) The hard part is knowing which dependencies to move with the package you want, and ensuring it's the version you want.

apt-get will happily tell you the answer to 3).
Your handy usb stick is a convenient answer to 2).

All the tools and apt-on-cd and apt-offline and apt-zip packages are simply ways to address those three issues. You can address them any way you wish.

---

