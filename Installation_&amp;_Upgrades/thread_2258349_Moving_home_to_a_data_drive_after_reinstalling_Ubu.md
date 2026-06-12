---
title: "Moving /home to a data drive after reinstalling Ubuntu 14.04 - Will it overwrite?"
date: 2014-12-26
forum: Installation &amp; Upgrades
---

### Post by Wolfsblood on 2014-12-26
Ok, so after blowing up my system trying to install Windows 7 as a dual boot (already having Ubuntu 14.04 installed) I needed to reinstall everything again. Now, I have a 120GB ssd where I have the os installed, and  a large sata drive where I store my data and programs. Previously I have gone through the steps to move the /home/user directory tree off of the ssd where the os was because 10 there wasn't room for all that, and 2) in the likely event that I broke something sobadly that it had to be reinstalled, I wouldn't lose everything. My concern now is whether or not redirecting the /home to the sata drive will keep the current directory tree intact, or overwrite it? In other words, will pointint /home to the other drive nuke it? I have reinstalled Ubuntu using the same username I did the first time, so /home/usr/ on both drives match. I have only installed steam and had Ubuntu run it's updates so far, and have been holding off on any other installations until I know whether or not it's safe to move the /home to a drive that already has that directory tree set up.

---

### Post by yancek on 2014-12-26
Are you moving home from the SSD to the external or is all your data already on the external drive?  It isn't clear whether you want to move data from the SSD to the external or just want to point the system to another /home partition on the external drive.  If it is the latter, you need a proper entry in the /etc/fstab file.

---

### Post by Wolfsblood on 2014-12-26
All mydata from the previous install is on the sata drive. /home currently points to the ssd where Ubuntu is installed. Ubuntu was already installed on the ssd, but due to me screwing something up, I had to wipe the sdd and start over again. Now I want to redirect /home from the ssd where it is now, to the sata drive where the old install pointed.   I would like the /home to point to the existing /home/usr directory on the sata.

---

### Post by grahammechanical on 2014-12-26
The simple way, in my opinion, to do this is to re-install Ubuntu to the SSD using the Something Else option and after telling the installer to install Ubuntu on to the SSD, then select the partition with /home/user on the SATA drive and give it a mount of /home but DO NOT mark it for format. Then nothing will be over written in the /home folders. And if you are using the same user name and password there should not be any problems.

There should be a command to do this but I have never used it. Although I used to have a  separate /home partition and and did re-install using the Something Else option. The important thing is to mark the /home partition with a /home mount point and to not format the partition.

Regards.

---

