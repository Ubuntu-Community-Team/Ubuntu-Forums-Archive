---
title: "Offline updating"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by bobbertface on 2008-06-09
I have a desktop with Hardy installed, and I want to update and upgrade it, however, it doesn't have a wired connection, and the wireless card is not supported by the kernel.  I tried installing ndiswrapper to fix this problem because my Dell Wireless 1505 Draft 802.11n WLAN Mini-Card Rev 2.0 is supported by it.  The fun part is, I need the c/c++ developer files to compile and install ndiswrapper.

What would be a good way to get those libraries over to the offline computer, or would using an already compiled ndiswrapper binary work fine? (if so, any recommendations as to which one works best?)

Thanks for any help you can provide

---

### Post by dstew on 2008-06-09
You only need to compile ndiswrapper if the most recent Ubuntu packaged verion is not adequate.

To update or install programs off-line, you need to be aware that there are lots of dependencies to be satisfied for installations to work. You can't usually download the package you want and install it, because it will complain that it needs all these dependent packages to be installed first.

There is a service called [**nonetdebs**]("http://nonetdebs.unixpod.com/") that attempts to solve this problem. You create a text file of the status of your off-line system, copy it over to an on-line system, and upload it to nonetdebs. The service prepares a bunch of links to all the packages you need to install in order to update, or install a particular package. You copy the packages onto a disk or USB stick, and copy them onto your off-line system, and install them using dpkg.

Try updating first, and see if you get a newer driver that might make your wireless card operational. If that doesn't work, try the **ndisgtk** program. I think it might be part of Ubuntu already, or you can install it. It is a graphical front-end for ndiswrapper that lets you navigate to where the Windows driver files are, and install them. To run it, hit alt-F2 and enter```
gksudo ndisgtk
```

---

### Post by _khAttAm_ on 2008-11-05
Why don't you try out:
[http://offlineubuntu.awardspace.com/](http://offlineubuntu.awardspace.com/)

It has step by step procedure to help you update and install packages to your offline ubuntu installation...

---

