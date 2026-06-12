---
title: "FIle system and eth0 questions"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2007-05-03
Are any of you familiar with mapping Ubuntu's file system with other Linux file systems?  For example, for class I have to display the contents of /etc/sysconfig/network-scripts/ifcfg-eth0, but of course this path does not exist.  The question is based off a version of Redhat.  I would like to know if there's any way to map the changes from directory to directory in different versions of Linux.  I tried using utilities like locate.

If anyone is familiar with the book I am using, it is Linux+ Guide to Linux Certification, Eckert & Schitka, 2003 (looks to be first edition).  Granted I probably should be using the version of Redhat that they distributed but I'm newb and Ubuntu appeals to newbs :)  Thanks for your time.

---

### Post by kidders on 2007-05-04
Hi there,

How to map out a filesystem, or map changes to a filesystem over time, depends on how much detail you want, and how you want to present the information. For instance, you could compare the contents of two tarballs (each representing the state of a filesystem at two different times) with **diff**, to enumerate each individual change. On the other hand, you may only be interested in relative differences in system directory sizes ... something which can be displayed nicely as a sort of pie chart.

For your class, it would certainly be worth considering installing the specific OS your teacher/lecturer is working with. Ubuntu and Red Hat will be perfectly happy to sit side by side on the same computer, so you could continue using Ubuntu for everyday purposes, if you wanted to. :-)

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

