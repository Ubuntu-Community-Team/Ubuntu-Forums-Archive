---
title: "No Root File System is defined"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by flatfish2 on 2015-05-05
During Installation attempted of UBUTU 14.04.2  I get this message " No root file system is defined please correct this from the partitioning menu"
On the window "Installation Type" the partition table is empty and the line under "Device for boot loader installation:" shows: /dev/sda  but I can't change anything.


 I have used GParted-live to format the HD :

/dev/sda1   ntf   ....................Window 7 
/dev/sda2   ext4     33GiB
/dev/sda3   linux-swap 3GiB

A Boot Flag is shown on the windows ntf partition.

By the way I have gotten the same error message after wiping the HD clean without the windows installation.

I also manually attached a Boot flag on the ext4 partition without success, same message: "No root file....."

where do I go from here?

Ubutu runs fine from the CD



Thanks for your help
John

---

### Post by yancek on 2015-05-05
If you have another operating  system installed such as windows, you will be much better off selecting the "Something Else" option when installing Ubuntu.  You should see a windows which lists whatever partitions/drives you have and since you have sda3 selected for Ubuntu, click the main windows to highlight that line then click the Change tab below  You will get an Edit partition window and there is an option to set the Mount point, select the first option which is the forward slash ( / ) symbold for the root of the filesystem.  This is all shown in the tutorial below, scroll about half way down the page.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by LostFarmer on 2015-05-05
Boot into the Live linux and in terminal run/  copy output and post
```
sudo parted -l
```    Note: l is a small L

---

### Post by flatfish2 on 2015-05-06
Thank you for your replies. Still working on my problem, I now understand about the need to set a Mount point but I couldn't even get to the something else menu, it goes right by it into the install menu.
I will start from scratch at a later time and get back.
Thank you 

John

I found this post by darkod and it solved my issue. Must have run Raid some years back
Thanks to all.

[COLOR=#000000][[IMG]http://ubuntuforums.org/customavatars/avatar946366_2.gif[/IMG]]("http://ubuntuforums.org/member.php?u=946366")[darkod]("http://ubuntuforums.org/member.php?u=946366") 
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]**Staff Emeritus****[IMG]http://ubuntuforums.org/images/rank_oldstaff_2013-02.png[/IMG]**


[RIGHT]Join DateNov 2009LocationSegur De Calafell, SpainBeans11,824DistroUbuntu 12.04 Precise Pangolin[/RIGHT]

[/COLOR]
[COLOR=#000000]**Re: No root file system defined**
[INDENT]Is the partitions list empty like on that video? You never mentioned that, you just said you get the no root filesystem message.

It is important information if the partitions list is empty. :smile:

Usually that happens if the disk has been used in raid before. Meta data remains are left on the disk which windows ignores but ubuntu doesn't.

If you ARE NOT running raid, boot into live mode with the ubuntu cd, open terminal and try:
Code:
sudo dmraid -E -r /dev/sda
If it asks you to remove raid meta data just confirm. After that the install should work fine.

Note that if you do the above and you ARE running raid, it will destroy your array and probably your data. You install on a raid system in different way. So, do NOT do the above if you are running raid.[/INDENT]


[/COLOR]

---

