---
title: "Install ubuntu on hp 8570w, problem with ubiquity"
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by umut-tabak on 2013-08-02
Dear all, 

I am trying to install ubuntu on my fresh hp 8570w laptop, however whatever I did, I could not manage to install. Attached is a screen shot of the error message with the details. Apparently, I have problem with ubiquity. Googling for some time also did not return any successful results. Any ideas on how to solve this install problem with my new laptop?

Greetz,
Umut

---

### Post by oldfred on 2013-08-03
Is this error on your installer booted in live mode, or after you have installed?

---

### Post by umut-tabak on 2013-08-03
> **oldfred said:**
> Is this error on your installer booted in live mode, or after you have installed?


This one was particularly in live mode where I would like to use the Gparted to partition my drive, however when I was trying to start the installation directly I was coming up to the partitioning point and at that exact point it was not possible to create a partititon table and I was getting exact the same error message there. Then I decided to partition the disk from live mode but that was also not possible, this is more or less the overview. I forgot to mention that my laptop came with Windows 7 preinstalled so maybe this is an important point so it has some ntfs partitions on that for windows already.

---

### Post by oldfred on 2013-08-03
Windows 7 systems almost always have used all 4 primary partitions, so you cannot install without deleting one primary partition with data (back it up first) and convert it to the extended partition which is a container for as many logical partitions as you want.

If you tried to create partitions with Windows it will convert to dynamic partitions which do not work with Linux.

Post this:

sudo parted -l

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)


 Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

