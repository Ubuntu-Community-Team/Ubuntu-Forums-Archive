---
title: "Dual Boot - Replacing LXLE with Xubuntu on a Windows Vista computer"
date: 2016-02-24
forum: Installation &amp; Upgrades
---

### Post by dave226 on 2016-02-24
Hi

Any suggestions would be gratefully appreciated.  I am fairly new to linux/ubuntu but liking it very much.  A while ago I installed LXLE alongside Vista with no problems.  I did the install as an automatic installation, i.e. I let LXLE decide on how to do the partitioning.  I would now like to replace LXLE with XUbuntu.  I am happy to overwrite LXLE completely.  I have XUbuntu on a USB pen drive but cannot decide on the best way to go about replacing LXLE with XUbuntu.  I am a little confused with the way the partitions are now set up and worried I may damage Windows.  The partitions are currently:

[TABLE="class: grid, width: 500"]
[TR]
[TD]63 MB
Healthy (EISA Configuration)[/TD]
[TD]Recovery (D:)
10 GB NTFS
Healthy (Primary Partition)[/TD]
[TD]OS (C:)
171.50 GB NTFS 
Healthy (System, Boot....)[/TD]
[TD]49.27 GB
Healthy (Prim Partition)[/TD]
[TD]2 GB Healthy (primary partition)[/TD]
[/TR]
[/TABLE]

The latter two partitions I am guessing relate to the LXLE installation; the second and third relate to Windows Vista; the first one (63MB).... I have no idea!


Should I:

[LIST=1]
[*]Use EasyBCD 2.3 to completely revert the partitioning back to when it just had vista on it and then install Xubuntu (as I did LXLE)? This would, I guess, involve merging the latter two partitions (above) to the OS (C:) partition.
[*]Can I use the USB pen drive which has Xubuntu and do an automatic install (the first choice on the installation)?  Will this just overwrite the previous linux installation (which I'm fine about) or will there be some complications with this.  I am less happy (at this stage) about deciding on the partitioning myself (the last choice on the installation)
[/LIST]

Any thoughts would be much appreciated.

Thanks
Dave

---

### Post by irvine_himself2 on 2016-02-24
IMHO, the simplest solution is always the best, which. in this case, would be merging the linux partion and its swap space back into the Vista partition. I think there is less potential for a serious mistake.  Best of luck  Irvine

---

### Post by oldfred on 2016-02-24
There was a bug in the installer in older versions, where it said it was only overwriting the previous Linux install, but erased drive.
Do not use an older version. And either way be sure to have good backups.

I suggest using Something Else, choose current / (root) as new / with change button. That should be all that is required.
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by dave226 on 2016-02-24
> **irvine_himself2 said:**
> IMHO, the simplest solution is always the best, which. in this case, would be merging the linux partion and its swap space back into the Vista partition. I think there is less potential for a serious mistake.  Best of luck  Irvine

Thanks for the quick reply.  I think that this is the route that I will take.  Can I just check.... am I right in thinking that from the table in the original post (or the attachment) that I would be just merging the last two partitions (49.27GB & 2GB) into the OS (C: ) partition?  Should I just leave the first partition alone (the 64MB)?  Cheers.

---

### Post by irvine_himself2 on 2016-02-24
As far as I can see, yes.

Depending on which partion tool  it may be a case of either merging, shrinking or deleting the partitions. Basically, you need to read the instructions for the tool that you are using.

Edit 
On the live CD, (or USB,) there should be a tool called Gparted to manage the partitions.

---

### Post by yancek on 2016-02-24
> am I right in thinking that from the table in the original post (or the  attachment) that I would be just merging the last two partitions  (49.27GB & 2GB) into the OS (C: ) partition?  

Does that mean you are now willing to overwrite your vista install?  Combining a windows partition with a windows filesystem (ntfs) with a Linux filesystem won't work.  The simplest thing to do if you want to install Xubuntu over LXLE is to install Xubuntu to the same partition and that certainly is not what you see as "C" or "D" in windows.  Boot the Xubuntu installation medium and open a terminal and run the command:  sudo fdisk -l (Lower Case Letter L in the command) and post the output here so that the partitions can be identified.  You would also be much better off using the Manual install method which is probably referred to as Something Else.  Might read the dual boot section at the link below.  It's specific to Ubuntu but I think Xubuntu uses the same installer.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by irvine_himself2 on 2016-02-24
> **yancek said:**
> ...............  Combining a windows partition with a windows filesystem (ntfs) with a Linux filesystem won't work. ......... 

That's not true, when you delete the two linux partitions, they become unformatted free space. Then, it is just a case of growing the Vista partition to use the space that has been freed. 

As far as using the "something else" installer option goes:

[LIST=1]
[*]In the past, it has been "buggy" 
[*]You really need to know what you are doing. (Noting I wanted to keep the factory reset partition, one of the many minor problems I have had with my replacement of Windows 10 with Wily Werewolf was understanding the warnings "something else" was giving me with respect to what Linux needed in the way of partitions.) 
[/LIST]

Having said all that though, you also need to think about the Grub2 bootloader, which would still be present after deleting the partitions. see here for how to do it with Windows 7:  [http://www.everydaylinuxuser.com/2015/01/how-to-recover-windows-7-and-delete.html](http://www.everydaylinuxuser.com/2015/01/how-to-recover-windows-7-and-delete.html)

So, ultimately, the best advice I can give you is: No matter which path you choose, "Be very careful and back up everything before you start."

Edit
Also read the instructions carefully, and plan exactly what you are going to do before you start. Having a printed workflow list is not a stupid idea.

---

### Post by T.J. on 2016-02-25
Welcome to the forums, Dave 226!

This is a guess but the first partition is boot partition, the second is your Windows recovery partition, the third is Windows, the fourth is Linux and the fifth is your Linux swap. You don't HAVE to reformat or anything though. :D

If you want to use XFCE instead of LXDE, I would just run these commands in a terminal:

*sudo apt-get install xubuntu-desktop xubuntu-artwork *

It will install XFCE/xubuntu in the same drive as LXDE, no repartitioning or anything required. Then just change the session type when you login from LXDE to Xubuntu/XFCE and it will start Xubuntu for you.  You might still see LXDE artwork when you boot/shutdown, but that is entirely cosmetic and won't affect using Xubuntu.

The only difference is which is installed by default, but you can have more than one interface (Xubuntu, Lubuntu, Kubuntu) in the same install.

---

### Post by dave226 on 2016-02-25
Just wanted to say thank you for all the good advice given.  Very impressed.  In the end I played it safe and went with merging the two LXLE partitions back into windows and then doing a clean install of XUbuntu via USB drive pen.  All works really well and pleased with XUbuntu.  Thanks again.

PS  Not sure if I have to mark this "solved" or how to do it.

---

### Post by yancek on 2016-02-25
> That's not true, when you delete the two linux partitions, they become unformatted free space.

Obviously deleting the Linux partitions will create free space then adding the free space to the other partition works fine.  I wouldn't refer to that as "merging" partition as you first need to delete to create unallocated space.

---

### Post by irvine_himself2 on 2016-02-25
Maybe a bad choice of words, but, as I pointed out, ultimately the exatct steps to "merge" a partion back into another while maintaining data/format integrity of the destination depends on the particular tool you are using. Similarly, I also pointed out that it is really important to read the instructions for said tool.

Edit
If you use Gparted, then it chains together multiple simple operations which are then applied as a single batch

---

### Post by T.J. on 2016-02-25
> **dave226 said:**
> Just wanted to say thank you for all the good advice given.  Very impressed.  In the end I played it safe and went with merging the two LXLE partitions back into windows and then doing a clean install of XUbuntu via USB drive pen.  All works really well and pleased with XUbuntu.  Thanks again.

PS  Not sure if I have to mark this "solved" or how to do it.

You're very welcome and I hope you will enjoy being a part of the community.  I believe there is a solved button near the top. Have a fabulous day ;D

---

