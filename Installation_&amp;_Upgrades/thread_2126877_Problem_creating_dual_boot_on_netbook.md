---
title: "Problem creating dual boot on netbook"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by glasseyefong on 2013-03-18
I'm trying to improve the performance of my underpowered and painfully slow Windows 7 Starter Samsung N150. I have a Lubuntu 12.10 install disk which works fine from the CD. Going through the early parts of the process, I am given 2 choices - replace or something else. The guides that I looked at on-line for earlier lubuntu versions had a "create dual boot" checkbox. As I am a techno dork can someone tell me how to achieve what I want?

Thank you

Martin

---

### Post by Rex Bouwense on 2013-03-18
I am dual booting on a netbook and one of the choices should be install Lubuntu 12.10 along side of Windows 7.  You are doing a normal install (not a wubi install) is that correct?
After booting from the CD you will be given several choices as you already know.  Go ahead and choose install unless you want to perform any other checks to insure that it is compatable with your computer.  After your choice of install, several other choices should pop up.  The one that you want is install along side of Windows 7.

---

### Post by Mark Phelps on 2013-03-18
IF your goal is to have BOTH Win7 and Ubuntu available on the netbook (something we call a dual-boot configuration), then do NOT use the Ubuntu installer to shrink the Win7 OS partition to make room for Ubuntu.  Doing so runs the risk of corrupting Win7 and rendering it unbootable.

So, before you jump into dual-booting, read through the details below ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by tejpatel98 on 2013-03-18
I am also dual booting off of a netbook and used the Wubi installer with no issues whatsoever.

---

### Post by glasseyefong on 2013-03-19
Thanks for the responses.

Rex/Tejpatel - I had to google Wubi. That's not what I've got (I think) but may be what I want. The guy who cut the disk for me said it would give me the install alongside option but I get just 2 choices, overwrite or something else.

Mark - I have 4 windows partions, System 100mg 71% empty, C: 67g 65%, D: 67g 100%, Recovery 15g 100%.
The install choice "Something else" takes me to a screen showing the partitions and options to change them and an "install now" button. I suspect whatever I do will overwrite Windows.

Is the Wubi route the option or is my problem the existing partitions?

RSVP

Martin

---

### Post by Rex Bouwense on 2013-03-19
WUBI was never meant for long time use (however some folks do use it for that).  It installs as you probably already know inside of Windows.  What you are looking for is a true dual boot and Mark has given you a road map for that.

---

### Post by oldfred on 2013-03-19
Almost all Windows 7 installs use all 4 primary partitions. You have to delete one to be able to create the extended partition. Then in the extended partition you can create many logical partitions and Linux works just fine from logical partitions. 
Details on HP, but every vendor is really the same. 

 Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by tejpatel98 on 2013-03-19
Are you looking to create a true dual boot, or just to try Ubuntu out and maybe keep it for a while?

---

### Post by glasseyefong on 2013-03-19
Thanks again for your replies in my attempt to create a true dual boot disk.

Presumably, if I only had 3 partitions I would get the option to install alongside Windows.

I looked at the links kindly supplied by OldFred and it certainly appears to be the cause of the issue I'm getting and a route to a solution.

I now need to convince myself that I have the ability and confidence to go through the processes.

Again, grateful thanks to all.

Martin

---

### Post by Theuinpo on 2013-06-02
> **Mark Phelps said:**
> IF your goal is to have BOTH Win7 and Ubuntu available on the netbook (something we call a dual-boot configuration), then do NOT use the Ubuntu installer to shrink the Win7 OS partition to make room for Ubuntu.  Doing so runs the risk of corrupting Win7 and rendering it unbootable.

So, before you jump into dual-booting, read through the details below ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

Mark -- I am a new LUBUNTU user as of about a week ago and I wanted to let you know that I greatly appreciated this post! I searched in vain for an approach to partitioning so that I could dual boot LUBUNTU and WINDOWS 7. I followed your method and it worked out great! Thanks much! 

Allen S.

---

