---
title: "Install ubuntu to drive other than C:"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by cochise7979 on 2008-03-22
I have a Ubuntu 7.1 DVD rom. It works fine. I have no problem booting and running from the DVD.
I want to install Ubungtu on the hard drive. I am using a 320GB hard drive which has 2 partions: C:/ 102GB, D:/ 202GB. I have Win XP installed on the C:/ . I want to install Ubuntu to the D:/ drive without disturbing anything on C:/  i.e. boot Windows from C:/ and boot Ubuntu from D:/. The install program won't allow me to do this, it wants to replace windows and repartion the C:/ drive. This is NOT acceptable. Can I get around this problem? If so specifically how?

Thanks in Advance
C. :confused:

---

### Post by nanotube on 2008-03-22
moved to the appropriate subforum...

---

### Post by Shazaam on 2008-03-22
First thing, forget the C: and D: WINDOWS lettering. It will confuse you to no end trying out linux. Also, when installing Ubuntu use either "Guided-resize" or "Manual" options during the partitioning phase.
What you will need to do is either delete the 202gig partition or resize it down and add a new partition.
Lets try something first. Write this command down on a piece of paper in case you don't have internet access running the Ubuntu livedvd.....
```
sudo fdisk -l
```
(small L and there is a space between sudo and fdisk, and between fdisk and -)
Boot the livedvd, open Terminal (Applications>Accessories>Terminal). In the window that opens type the command in and hit enter. If you have a working internet with the livecd copy/paste the output of terminal here. If you don't, write it down so you can post it here. What this code does is print out your partition list.

Here are some links for you to read (don't let the first one scare you off).
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by cochise7979 on 2008-03-25
> **Shazaam said:**
> First thing, forget the C: and D: WINDOWS lettering. It will confuse you to no end trying out linux. Also, when installing Ubuntu use either "Guided-resize" or "Manual" options during the partitioning phase.
What you will need to do is either delete the 202gig partition or resize it down and add a new partition.
Lets try something first. Write this command down on a piece of paper in case you don't have internet access running the Ubuntu livedvd.....
```
sudo fdisk -l
```
(small L and there is a space between sudo and fdisk, and between fdisk and -)
Boot the livedvd, open Terminal (Applications>Accessories>Terminal). In the window that opens type the command in and hit enter. If you have a working internet with the livecd copy/paste the output of terminal here. If you don't, write it down so you can post it here. What this code does is print out your partition list.

Here are some links for you to read (don't let the first one scare you off).
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I'm still working on this. I read the links, I have been running Ubuntu for a short time (3 mos.) but on a computer where Linux is the only system. I'm trying to set up a new system as dual boot. I want the 202GB partion for Ubuntu only. I don't mind resizing and reformating that partion only. I haven't got it figured  out yet.

Thanks
C. :)

---

