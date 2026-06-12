---
title: "Gparted cant't resize ntfs partition with WinXP"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by iSleipnir on 2007-02-24
I'm currently trying to install Ubuntu Edgy on a laptop with a single ~93 gig hdd in one partition. It has Windows XP installed in it, and I've been having trouble using gparted to resize the partition. 

I boot from the live CD and choose to manually resize the partition when gparted loads. 
About 48gigs are in use and every time I try to make a the partition 25gb's smaller it spits back an error 

"an error occurred while applying the operations"
 "the following could not be applied to disk" 
(resize , disk info, etc)



I've tried disabling the unmovable swap and hibernate files in winXP and then defragmenting. If the defragmenter graphics are any indication all the the disk info looks to be on the first half of the disk.

I've run disk check on the windows install until it says no errors were found on the disk. And gparted still will not partition the hdd. The specific error says 

"check filesystem for errors and (if possible) fix them"

even though I just did check the hdd and there were no errors. 



I'm out of ideas on how to repartition this hdd, so I'm wondering if anybody else has any solutions to this problem? Thank you for your time,

-Nick

---

### Post by Spin Doctor on 2007-02-24
I had the same problem as you are having. Wanting to resize a NTFS partition.

The solution I found was to use the Alternative Install CD for edgy, and go to rescue system prompt, and after entering a username and getting network setup, press escape to get you out to the main meny, and then select the partioner, and use that tool to resize your NTFS partition. Make sure all the mountpoints are correct aswell. 

Like any partion work..Do your a backup BEFORE =)

Hope this could be any help to ya! Goodnite from Sweden!

---

### Post by iSleipnir on 2007-02-24
That sounds like it might work. I've searched around a bit but can't seem to find the location of a alternate install cd. Do you happen to have a link?

And thanks for the help, I'm pretty new to this.

---

### Post by confused57 on 2007-02-24
> **iSleipnir said:**
> That sounds like it might work. I've searched around a bit but can't seem to find the location of a alternate install cd. Do you happen to have a link?

And thanks for the help, I'm pretty new to this.

You might want to try the gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It's only a 30 mb download, has a later version of gparted than the desktop live cd and is better able to resize NTFS partitions...might be worth a try.

If you still want to try the alternate cd, select a mirror close to you:
[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

---

