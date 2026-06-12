---
title: "Install Lucid 64-bit on special RAID"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Rommsey on 2010-04-30
Hi all, I'd first like to say thanks for a wonderful community and resource dedicated to helping people with Ubuntu and that it's a real treat to become a new member.

As per my issue, I did some browsing on how to install Ubuntu on fakeraid and was unable to find a resource that addresses my situation. What I would like to do is install Lucid on my computer so that Windows 7 is my primary OS and I can dual boot into Ubuntu on my non-OS drives at will. I think this sounds fairly confusing. :lolflag:

I have the following setup:

2xSSD in RAID 0 Games_OS (my OS RAID)
2xHDD in RAID 0 Games_Storage (my Storage RAID)
1xSSD not in RAID (Game drive)

Basically what I would require is that I can install Lucid on my Games_Storage RAID. Upon opening up a terminal, I notice that Ubuntu already has my RAID set as active.

ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_cdadahbihg_Games_OS" already active
RAID set "isw_ifjaefbad_Games_Storage" already active
RAID set "isw_cdadahbihg_Games_OS1" already active
RAID set "isw_cdadahbihg_Games_OS2" already active
RAID set "isw_ifjaefbad_Games_Storage1" already active
RAID set "isw_ifjaefbad_Games_Storage2" already active
RAID set "isw_ifjaefbad_Games_Storage5" already active
RAID set "isw_ifjaefbad_Games_Storage6" already active
RAID set "isw_ifjaefbad_Games_Storage7" already active

I have a set amount of space reserved for Ubuntu on my storage drive and I would like to build my sub-partitions within that area to house my Linux install. I am using the LiveCD install method.

I am stuck at the Prepare installation screen and I do not want to risk wiping anything to get my install done. I have attached a screenshot to show where I am at in the process:

[IMG]http://ubuntuforums.org/%3Ca%20href=http://img188.imageshack.us/i/screenshotinstall.png/%20target=_blank%3E[IMG]http://img188.imageshack.us/img188/4483/screenshotinstall.png[/IMG][[IMG]http://img188.imageshack.us/img188/4483/screenshotinstall.png[/IMG]]("http://img188.imageshack.us/i/screenshotinstall.png/")

Any thoughts or suggestions?

I apologize ahead of time if this is covered elsewhere but I have not been able to locate a resource here and elsewhere on the internet.

---

### Post by Rommsey on 2010-05-01
Anyone? ](*,)

---

### Post by Rommsey on 2010-05-03
Daily bump!

Is this possible?

---

### Post by Rommsey on 2010-05-04
Any ideas guys?):P

---

### Post by Rommsey on 2010-05-05
Bump for some help! :D

---

