---
title: "'Install Ubuntu Alongside Windows7' is not given"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by dp7 on 2011-05-26
Hi Guys,

Need help. While istalling Ubuntu, after choosing the language, I do not have an option 'Install Ubuntu alongside Windows7'. What could be a problem?

Thank you.

dp7

---

### Post by oldfred on 2011-05-26
Welcome to the forums.

How many partitions do you have. The auto installer has to be able to shrink windows and create an extended partition to put the logicals into. Most windows 7 installs have used all 4 primary partition under MBR type partitioning scheme. You have to have one primary as an extended.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by dp7 on 2011-05-27
Thanks for your advice. Unfortunately MS's Disk Management does not allow me to partition hard drive. (As far as I understand the problem is NTFS file system format). 

So I phoned MS support. Initially they sounded optimistic, but after wasting 1 hour of my time they started to come up with excuses and at the end insisted that in CANNOT be done. I asked them to send me an e-mail which is listed allow.


'Sir just to let you know you won’t be able to format base C drive on GUI mode. You can create a part ion of C drive only while booting from Windows disc and deleting C drive but then you will lose Windows. 
Thanks and Regards,
Hemant Singh'

Please advise on my other options.

Thank you.

denis

PS. Cannot wait to get break free from MS's nonsense.

---

### Post by dp7 on 2011-05-27
Just in case, I have Dell M1330

---

### Post by oldfred on 2011-05-27
You only want to use Windows Disk Management to shrink windows main partition. If you create partitions with windows it auto converts to sfs or dynamic partitions which is like logical volumes. SFS is only compatible with windows and not even all windows.

Post this from liveCD:

sudo fdisk -lu

---

### Post by dp7 on 2011-05-27
MS's 'Disc Management' doesn't allow me to shrink. Pls see screenshot attached.

---

### Post by oldfred on 2011-05-27
You do not have any free space to shrink. It shows 17% available but if windows gets below about 10% it slows to a crawl, you actually should increase free to 30% with NTFS if you want good performance with windows.

Time for a new hard drive and then you can have windows on one & Ubuntu on the other.

---

### Post by dp7 on 2011-06-17
At the end I had to format hard drive and reinstall W7 and then  to install Ubuntu. Didn't come back to W7 since though:P

---

