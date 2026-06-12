---
title: "Problem in installing ubuntu 11.04"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by arka.sharma on 2011-09-25
Hi,
 
   I am facing some issue in installing ubuntu 11.04.I already have ubuntu 8.10 installed on my /dev/sda6.I have downloaded ubuntu 11.04 from ubuntu.com and burned the .iso image in a cd.I restarted and boot from the cd.All was going right.When the partition manager appeared I deleted /dev/sda6 and created a new partition with same ext3 file system and clicked "install" button it shows a message box saying

"The installer needs to commit changes to partition tables,but cannot do so because partition on the following mount point couldn't be mounted

/cdrom

Please close any applications using these mount points.

Would you like the installer to try to unmount these partition again ?"

When I clicked continue it was only showing "detecting file system" but no progress was there.What may be the issue and how to fix it?

Thanks

---

### Post by dino99 on 2011-09-25
how i do:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by arka.sharma on 2011-09-25
Thanks for your reply.I allocated 18 gb mounted at '/' and selected ext3 file system along with 3 gb swap area.But i'm not getting the message 

"The installer needs to commit changes to partition tables,but cannot do  so because partition on the following mount point couldn't be mounted

/cdrom

Please close any applications using these mount points.

Would you like the installer to try to unmount these partition again ?"

Is the cd not properly burned ? Or is it the issue with the previous ubuntu that is installed

---

### Post by necromonger on 2011-09-25
here is how i install linux.nixi will show you how.
[http://www.youtube.com/watch?v=GhnLk3gviWY&feature=relmfu](http://www.youtube.com/watch?v=GhnLk3gviWY&feature=relmfu)

---

### Post by garvinrick4 on 2011-09-25
Boot off of Live Cd (install Cd using Try Ubuntu) and open a app called "gparted" and
take a screenshot of it and use the attachment (paper clip) and upload screenshot
and hit submit, will not see screenshot til then after upload. So users can see what
you have on partition table.
Did not have to delete partition should have just installed in same one and checked format
box and mount point of / and in ext4. Will just install in same partition. So lets take a look
and see easiest way for you to install. I will be online for a bit and if I am not there are a 
lot of users can give instructions. This Forum is not like other Forums it is a busy Forum
with knowledgable users and some even know how to spell knowledgable, not like me.

#If I am not here and dino99 is and has this Thread subscribed he will get when you post and you
will have a real nice user to help you.

---

### Post by oldfred on 2011-09-25
It also may be related to swap. LiveCDs like to use an existing swap to speed things up as Hard drive is faster than CD. But if swap is in the extended partition it may still be mounted and causing issues.

From liveCD gparted click on swap and right click swap off. 

I have normally heard that having an existing swap speeds up installs, so that may not be the issue.

---

### Post by arka.sharma on 2011-09-26
Thanks all for your reply.But why the following message is coming 

"The installer needs to commit changes to partition tables,but cannot do  so because partition on the following mount point couldn't be mounted

/cdrom"

Is it because the previously installed 8.10.One thing I must add here that when the "edit partition option" comes up I have deleted the partition caontaining ubuntu 8.10 mounted at '/' having ext3 file system.I deleted that partition from there.But 8.10 is still there intact.

Thanks,
Arka

---

### Post by arka.sharma on 2011-09-26
One important thing I forgot to mention is that my processor is Intel i3 64 bit and I'm trying to install Ubuntu 11.04 32 bit.But that shouldn't be an issue.I also found in ubuntu installation document that for 32 bit architecture size swap partition maximum is 32 bit.But that yet shouldn't be an issue cause my underlying processor is 64 bit.

---

