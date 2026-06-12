---
title: "e-mail regarding ethernet firmware being corrupted by Intrepid Alpha 6"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wpshooter on 2008-09-24
Can someone give me the scoop on this e-mail that I received this morning regarding the possibility that there is a bug in the latest Alpha 6 version of Intrepid that may possibly corrupt the firmware of the Intel ethernet connector / hardware device ?

I wonder how widespread this problem might be.

How would I know if this may have happened on a machine that I had been using to test Intrepid Alpha 6 and more importantly if the firmware of my ethernet connector has been corrupted, how would I go about fixing it ?

Thanks.

---

### Post by overdrank on 2008-09-24
Hi and this may help
[http://ubuntuforums.org/showthread.php?t=927944](http://ubuntuforums.org/showthread.php?t=927944)
Moved :)

---

### Post by wpshooter on 2008-09-24
> **overdrank said:**
> Hi and this may help
[http://ubuntuforums.org/showthread.php?t=927944](http://ubuntuforums.org/showthread.php?t=927944)
Moved :)

I get a "you are not authorized to access this page" message when I try this link.

---

### Post by ssam on 2008-09-24
if your wired network still works then you are fine.

the link above seems wrong.
see [http://ubuntuforums.org/showthread.php?t=927943](http://ubuntuforums.org/showthread.php?t=927943)

you can also keep an eye on
[http://news.gmane.org/gmane.linux.ubuntu.devel](http://news.gmane.org/gmane.linux.ubuntu.devel)

looks like the intel devs are getting close to tracking this down.

its also worth noting that there are only a small number of reports of this happening.

---

### Post by scooternew on 2008-09-24
From what i understand this only affects the e1000e driver on the 2.6.27 kernel.

This is a link to the upstream kernel bug:
[http://bugzilla.kernel.org/show_bug.cgi?id=11382](http://bugzilla.kernel.org/show_bug.cgi?id=11382)

This is a link to the launchpad bug report: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555)

Link to Mandrivia's notice page tells you how to determine if you have a e1000e network card:
[http://blog.mandriva.com/2008/09/23/urgent-notification-major-bug-in-all-mandriva-linux-2009-pre-releases/](http://blog.mandriva.com/2008/09/23/urgent-notification-major-bug-in-all-mandriva-linux-2009-pre-releases/)

---

### Post by caryb on 2008-09-24
Well I got bitten! perhaps this should be a lesson for me to check 1st! I must admit I never thought of destruction when it comes to updates. I do have a life saver & SMC USB ethernet adaptor, it comes in handy when you are building servers & drivers aren't yet in the kernel, it allows you to install & download the appropriate driver:) 

When I type lspci I get Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)

Is this good???


Cary

---

