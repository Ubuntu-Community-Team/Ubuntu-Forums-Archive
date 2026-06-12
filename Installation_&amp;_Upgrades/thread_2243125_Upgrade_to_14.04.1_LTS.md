---
title: "Upgrade to 14.04.1 LTS"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by Shadius on 2014-09-06
Hey everybody,

So I got the prompt to upgrade to 14.04.1 LTS. My concern is what will happen to my files once I do upgrade. Will I lose them? I have a ton of pictures and music on the computer that I definitely cannot lose! So can someone point me to where I can get information about the upgrade process. Much appreciated!

---

### Post by Old_Grey_Wolf on 2014-09-06
Always backup important files before doing an upgrade.

---

### Post by roger_1960 on 2014-09-06
Hi

If it goes as it should, all your data and applications will be preserved.  BUT back it up as advised because it might not work......

Roger

---

### Post by Shadius on 2014-09-06
Okay. Thanks for the tips. Have any of you experienced a time when it didn't go as it should?

---

### Post by yancek on 2014-09-06
I would also say to backup anything important to an external medium before doing an upgrade.
I've done upgrades of Ubuntu several times without problems but there is no way it can be guaranteed to work.
If the most important data you have is Pictures and Music, why not create a separate partition on which to place them.  Then an upgrade or new install won't overwrite that data as it won't be on the same partition as your installation.  You could create the partitions and copy/move your Pictures and Music before you do the upgrade.

---

### Post by Old_Grey_Wolf on 2014-09-06
> **Shadius said:**
> Okay. Thanks for the tips. Have any of you experienced a time when it didn't go as it should?

I have had some fail. There was a poll on the forum that could give you an idea [here]("http://ubuntuforums.org/showthread.php?t=2217531").

45.5% of the upgrade were successful.
33.8% of the upgrades had minor problems.
20.8% of the upgrades had problems the person couldn't fix.

---

### Post by Shadius on 2014-09-06
> **yancek said:**
> I would also say to backup anything important to an external medium before doing an upgrade.
I've done upgrades of Ubuntu several times without problems but there is no way it can be guaranteed to work.
If the most important data you have is Pictures and Music, why not create a separate partition on which to place them.  Then an upgrade or new install won't overwrite that data as it won't be on the same partition as your installation.  You could create the partitions and copy/move your Pictures and Music before you do the upgrade.

This sounds like a good idea. How do I go about doing this? I have a 1 TB HDD. I had wanted to initially make a boot partition and then just have the rest of the drive with my files on it.

---

### Post by Old_Grey_Wolf on 2014-09-06
You could move all of you personal files to a separate /home partition. Here is the Ubuntu [documentation]("https://help.ubuntu.com/community/Partitioning/Home/Moving").

---

### Post by Shadius on 2014-09-06
> **Old_Grey_Wolf said:**
> You could move all of you personal files to a separate /home partition. Here is the Ubuntu [documentation]("https://help.ubuntu.com/community/Partitioning/Home/Moving").

Thank you!

---

### Post by yancek on 2014-09-06
The first link below is a tutorial on using GParted, the partition manager which is available on any Ubuntu installation medium.  The second link is a detailed How to Install Ubuntu 14.04 which contains a lot of useful information at the beginning of the page. 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

Having a second drive just for backups would be better.  If that isn't an option, read the tutorials at the links I've posted.  Before anyone here could give you specific suggestions on what to do, you would need to post information on your partitions from either gparted or the fdisk command output.

---

### Post by Shadius on 2014-09-06
> **yancek said:**
> The first link below is a tutorial on using GParted, the partition manager which is available on any Ubuntu installation medium.  The second link is a detailed How to Install Ubuntu 14.04 which contains a lot of useful information at the beginning of the page. 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

Having a second drive just for backups would be better.  If that isn't an option, read the tutorials at the links I've posted.  Before anyone here could give you specific suggestions on what to do, you would need to post information on your partitions from either gparted or the fdisk command output.

Okay, I'll post the information about how my current partitions are set up and perhaps I can be guided on what's the best approach. Thanks a bunch for the information!

---

