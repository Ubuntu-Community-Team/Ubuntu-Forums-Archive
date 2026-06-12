---
title: "Dualboot and partitioning"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Tovam on 2009-12-26
Hello
Right now, I have a 500GB internal HD with Ubuntu and (a broken) WinXP, but I want to reinstall it because of some issues.

I have a new 320GB HD, and am planning to install both boots on there. After that, I can easily move whatever settings and files I need from the 500GB to the 320GB, and fragment the 500GB to serve as data storage.

The new boots will be Ubuntu, probably 9.10 for everyday use, and Win7 for games and .NET programming.

My questions;

* What is the best way to partition the 320GB? I was thinking of something like...

/dev/sda1 /win ntfs 250GB
/dev/sda2 extended
/dev/sda3 /swap ext4 4GB
/dev/sda4 / ext4 26GB
/dev/sda5 /home ext4 40GB

Or should I leave some unallocated disk space?

* Would it be a bad idea to set the Ubuntu home partition to be the Windows My Documents as well? (I'd say it is, but this one is mostly curiosity.)

* How do I set my 320GB to be the primary drive, the one to boot from? Is it in the bios? Because I don't believe SATA has master/slave.

* Is there anything I am overlooking?

Thanks in advance.

---

### Post by jSalv on 2009-12-26
I would suggest using Win XP instead of 7, to start with.

About the partitioning, I really don't know... but 40GB swap shouldn't be necessary, I think less is enough.
The second: I'd say it is a bad idea compared to it having its own partition.
When dual-booting it should let you choose the partition at every boot.
Not that I know of, but again, I know very little :D

---

### Post by phillw on 2009-12-26
> **Tovam said:**
> Hello
Right now, I have a 500GB internal HD with Ubuntu and (a broken) WinXP, but I want to reinstall it because of some issues.

I have a new 320GB HD, and am planning to install both boots on there. After that, I can easily move whatever settings and files I need from the 500GB to the 320GB, and fragment the 500GB to serve as data storage.

The new boots will be Ubuntu, probably 9.10 for everyday use, and Win7 for games and .NET programming.

My questions;

* What is the best way to partition the 320GB? I was thinking of something like...

/dev/sda1 /win ntfs 250GB
/dev/sda2 extended
/dev/sda3 /swap ext4 4GB
/dev/sda4 / ext4 26GB
/dev/sda5 /home ext4 40GB

Or should I leave some unallocated disk space?

* Would it be a bad idea to set the Ubuntu home partition to be the Windows My Documents as well? (I'd say it is, but this one is mostly curiosity.)

* How do I set my 320GB to be the primary drive, the one to boot from? Is it in the bios? Because I don't believe SATA has master/slave.

* Is there anything I am overlooking?

Thanks in advance.

hi, leave your win on sda1
pop your root ubuntu onto sda2
make sda3 extened
put your swap and /home onto the extended area
so, it'd be

sda1  Win
sda2  /  Ubuntu  about 10GB
sda3  extended
sda5 /swap
sda6 /home  as much as you want

As for unallocated ... Depends on how much room you have
/swap needs to be 1GB or whatever your RAM is (whichever is greater)
you can set a partition up for quick backups when you want to try something that may break your computer.

But, as you have a 2nd hard drive, I'd put the backups on that one - that way, if a disk fails you have your important stuff (**/** and **/home** on there - you can backup your other stuff as you want.

Phill.

---

### Post by Tovam on 2010-01-01
Thanks for the replies.

One more question. What would be the best way to partition the drive?
Partition it using gparted from the old boot? Install new Ubuntu first, and partition it using the build-in partitioner? Or install Win7 first, and use their partition manager?
Is it even possible for 7's partition manager to do all that?

And thanks for the advice on installing XP instead of 7, I know it's the smartest, but I need some things on 7, and XP has let me down before.

---

### Post by raymondh on 2010-01-01
> **Tovam said:**
> Thanks for the replies.

One more question. What would be the best way to partition the drive?
Partition it using gparted from the old boot? Install new Ubuntu first, and partition it using the build-in partitioner? Or install Win7 first, and use their partition manager?
Is it even possible for 7's partition manager to do all that?

And thanks for the advice on installing XP instead of 7, I know it's the smartest, but I need some things on 7, and XP has let me down before.

Just my .02 thought ...

Create the partitions beforehand using gparted from the liveCD.  For win7, make the space NTFS. For Ubuntu, I would make everything (swap, root and /home) logical partitions inside an extended.  For swap, I'd use 2gb.  For root, i'd use 10gb.  The rest for /home.  My format would be ext3 for root and ext3 for /home.  Then,  I'd boot into win7 install DVD and install win7 unto the NTFS partition.  When done, I would reboot into windows and make sure everything is OK.  Only then would I install Ubuntu.... choosing the manual method in step 4.


Of course, I would back-up my files first.

Lastly, when using gparted, make sure you identify and select the proper HD in the upper-right box.

Just sharing my method.  :)

---

### Post by Mark Phelps on 2010-01-02
For my .02 worth ...

I heartly recommend using Win7 instead of XP -- if you're going to do a new install.

Unfortunately, the only way that you'll know for sure if your hardware and apps work with Win7 is to install it.  Since your XP install is not working, you can't use the Win7 checkout tool to see what would need to be replaced.

An alternative, if you want to go to the trouble, would be to reinstall XP, use the Win7 tool to see what needs to be replaced, and if everything appears to be OK with upgrading, getting the XP upgrade tool from LapLink.  It will allow you to do an upgrade from XP to Win7 -- somethig that MS will not support on its own.

---

### Post by KPDXHAM on 2010-01-04
Tired of messing with WUBI and want to leave XP on Main HDD and do a fresh install of Ubuntu on second HDD.
In another thread I read about physically disconnecting the main drive, then connect the second (slave) as the main (primary) HDD, then install Ubuntu.
I tried this.

[LIST=1]
[*]Before making any changes, I used the Ubuntu live cd with Gparted to format to ext3 the entire HDD(slave) that I use for Ubuntu since I've read that Linux runs better on ext3 than ntfs.
[*]Then shut-down and removed the live cd.
[*]Opened computer case (desktop) and disconnected power & cable to primary HDD.
[*]Connected IDE cable to the other "Ubuntu" HDD as Primary, along with power of coarse.
[*]Then booted with Ubuntu cd and found that there's a few more folders to put somewhere than just the root, boot, swap and home.
[/LIST]
Also, I couldn't figure out how to make an extended partition and then add folders to it. 
And, I noticed that since this HDD was in the primary position it was labeled sda, so would it automatically show as sdb after reconnecting it to the slave position with the original xp HDD in primary position? Otherwise there would be a problem with xp.

Sorry for sounding so stupid, but this Linux stuff is new territory for me.
I have almost 200 bookmarks for Ubuntu since March 2009 as I try to get this Ubuntu OS squared away as my primary OS. 
I'm really impressed by what can be done with it compared to M$! Cleaner, faster system than M$ from what this amateur can see...and FREE too! 

Thank you! To all those of you out there who have the patience and concern to help dummies like me! :confused:

---

### Post by oldfred on 2010-01-04
I may be better to leave the windows drive plugged in as slave and keep it as slave. Grub will find it and set it up to boot so it thinks it is still first with some devicemap  commands.

Grub also has trouble finding a second drive if it was not plugged in originally. The device.map file does not list all the drives and has to be updated.

Computers only boot from whatever drive is first in BIOS or the first master with older IDE systems. If you switch drives back you will boot windows and not see Ubuntu. Grub will let you select which to boot.

You should not need a /boot unless your system is pretty old and the drive is large. I forget exactly how to create an extended partition but it is just another partition that holds other partitions. I think it was a choice when formatting since you do not format it, kinda like swap it is just a choice.

Too much info, but all of it is usefull:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

---

### Post by KPDXHAM on 2010-01-04
Thanks Old Fred! I really appreciate the help!
I'll check it out.
Being unemployed for about 12 weeks now and nothing on the horizon, I should have time.

Problem I seem to have is too much info, not enough brain power. ](*,)
I'm sure that if I can just get a simple picture of how it all fits together and then make it work, then things will be great.

Reminds me of about 20 years ago when we bought our first PC, used, no operating disks with it, just junk disks. And DOS. What's that??
No internet, so I went to local library and checked out 3 books on computers. Well, all I wanted to know was "How do I use this thing?" Two of the books were over my head. One book that helped was called DOS For Dummies. I didn't even have to read the whole book to know what to do.
Kind of like learning to drive a car without knowing all the details of carburetion, combustion, power differential, etc.. Here's the key, put it in there and turn, etc,.....
Just basics.

---

### Post by Tovam on 2010-01-05
Thanks for the help everyone. I'm still [struggling]("http://ubuntuforums.org/showthread.php?t=1373432") with installing both OSses, but the partitioning went nicely.

---

### Post by KPDXHAM on 2010-01-06
> **oldfred said:**
> I may be better to leave the windows drive plugged in as slave and keep it as slave. Grub will find it and set it up to boot so it thinks it is still first with some devicemap  commands.

Grub also has trouble finding a second drive if it was not plugged in originally. The device.map file does not list all the drives and has to be updated.

Computers only boot from whatever drive is first in BIOS or the first master with older IDE systems. If you switch drives back you will boot windows and not see Ubuntu. Grub will let you select which to boot.

You should not need a /boot unless your system is pretty old and the drive is large. I forget exactly how to create an extended partition but it is just another partition that holds other partitions. I think it was a choice when formatting since you do not format it, kinda like swap it is just a choice.

Too much info, but all of it is usefull:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

Thanks again Old Fred! This is Old Cliff...;)
I looked through your links and founds lots of helpful stuff, but just have one ..or two questions.

[LIST=1]
[*]Why does it show sda HDD in this frame when the only drive I partitioned and have set to format is sdb HDD?
[*]Is this the way it should look?
[/LIST]
I'm not formatting anything until I know that I won't mess up XP. I don't have a place to back it up to.

[[IMG]http://img19.imageshack.us/img19/4018/notreadytoinstall.png[/IMG]]("http://img19.imageshack.us/i/notreadytoinstall.png/")

---

### Post by KPDXHAM on 2010-01-06
Tried and failed to install twice.](*,)


[http://picasaweb.google.com/CliffHammer/FailedUbuntuInstalls?authkey=Gv1sRgCN7_4ZSko6C2zgE&feat=directlink](http://picasaweb.google.com/CliffHammer/FailedUbuntuInstalls?authkey=Gv1sRgCN7_4ZSko6C2zgE&feat=directlink)

First I tried with the /home at about 30GB
Then when it showed there was not enough room for /target/var/lib/dpkg/info/passwd.conffiles', I figured I just needed to enlarge the partition that has /home/tmp/usr/var/srv/opt/usr/local

So I started over and made that partition about 80GB, but as you can see in the pictures, this didn't fix the problem. :(

---

### Post by oldfred on 2010-01-06
I do not remember this screen but then I formated with gparted first and blew by the partitioning & formatting on my last install. It does say it is only formatting the sdb partitions. Also the advanced button will let you install grub to sdb if that is not the default boot drive. You then could make sdb the boot drive. grub2 prefers to boot from the same drive or the grub in the MBR and Ubuntu should be on the same drive and to boot with grub that has to be the first drive in BIOS or primay master in the ide chain.

---

### Post by KPDXHAM on 2010-01-07
**Got it!** \\:D/

Here's what really helped clear things up for me:
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

Watching the videos by Alan Pope regarding

[LIST]
[*]Ubuntu Partitioning
[*]Ubuntu Dual Boot Install
[/LIST]
Here's how I "thought" it should look:
[[IMG]http://img80.imageshack.us/img80/4316/6secondfailedinstallm.th.png[/IMG]]("http://img80.imageshack.us/i/6secondfailedinstallm.png/")

And here's what Alan showed:
[[IMG]http://img63.imageshack.us/img63/2755/screenshotubuntuubuntus.th.png[/IMG]]("http://img63.imageshack.us/i/screenshotubuntuubuntus.png/")

Here's what I came up with:
[[IMG]http://img63.imageshack.us/img63/4483/screenshotinstall.th.png[/IMG]]("http://img63.imageshack.us/i/screenshotinstall.png/")

Here's what it looked like in Gparted:
[[IMG]http://img37.imageshack.us/img37/4672/newinstall010610.th.png[/IMG]]("http://img37.imageshack.us/i/newinstall010610.png/")

I was surprised when I saw the extended partition in Gparted since I had not made one in the Ubuntu installer.
I had made the FAT32 partition thinking that with ext3 or 4 I would not be able to transfer files between my xp hdd and Ubuntu. I was wrong! After I found that I could transfer directly between the two hdd's I removed the Win partition (FAT32), removed the swap, and extended partition, then enlarged my /home while using Gparted on the Ubuntu live cd.
 [[IMG]http://img52.imageshack.us/img52/2115/modifiedsdbgparted.th.png[/IMG]]("http://img52.imageshack.us/i/modifiedsdbgparted.png/")

Now, to reinstall and tweak my Ubuntu system back to what I had before I screwed it up mis-using Sbackup on a Wubi installation where (so far) I've not been able access that system. :(

Thanks to all you folks out there who help us amateurs! 
Very much appreciated!:D

---

