---
title: "How to install vista along with existing Ubuntu 10.04"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by s-valley on 2010-08-08
On my system I have ubuntu 10.04 installed (when I bought a new hard drive)  when I was installing I made partitions and installed it in one of the partitions.  Now I want to install windows vista on the other partition to use quick books and NeatWorks.  When I try to install Vista with recovery cd it says it is going format the disc.  

Please advice me how to install vista without losing my ubuntu.

---

### Post by oldfred on 2010-08-08
Probably not:

Most recovery disk are not install disks but just an image of the drive as you purchased it. It just reinstalls that image erasing everything and making it like "brand new". 

You should backup /home, make a list of all installed programs and any edits you did to config files systemwide in /etc. 

You also can use programs like remastersys to make an image of your Ubuntu install.

Make live CD or DVD
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
[http://clonezilla.org/](http://clonezilla.org/)

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)


from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

 dpkg --get-selections > ubuntu-files

---

### Post by computerfreak4284 on 2010-08-08
Since u installed ubuntu first there is no way to install vista alone side it without messing up ur linux. Backup ur data and redo the PC with vista first then do linux.

---

### Post by s-valley on 2010-08-09
Thank you very much for the help.  I installed vista which formated the drive.  Then I re-installed ubuntu.  Thanks for explaining how to get back to all the installed packages and data.  Without your help I couldn't have done it.

Thanks a lot.

---

