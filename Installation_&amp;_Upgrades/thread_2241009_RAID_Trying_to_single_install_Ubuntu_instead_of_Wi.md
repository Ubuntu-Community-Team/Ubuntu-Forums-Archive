---
title: "RAID: Trying to single install Ubuntu instead of Windows xp"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by Peter_Mars on 2014-08-23
**[B]&#8203;**&#8203;[/B]I got an old pentium dual core computer running at 3 ghz and 1gb ram system memory. Now I am trying to install Ubuntu on it (don't need any data from drives). 
They however are formated as a raid 0 . Thinking I could just format the new drives I started up the ubuntu install and got a ??  error after chosing the erase all data and install ops. So I chose to go to Bios and deactivated the Raid 0 changed Sata options from auto raid to look for sata/pata drives only. It automatically found a drive although naturally not beeing able to boot from it. (There are two drives in the computer one on Sata 2 the other 4 slot). Now I retried after the same step (the erase all data and install) I again got an ?? error with no explanation.

The computer has a 32bit ops and i chose the 32 bit ubuntu ops. I am trying to install from disk and the ops runs just fine in disk mode. I actually really like ubuntu but I am just out of knowledge. I have no Windows xp disc to erase all data although I could prob find a version somewhere. But if anyone has a different solution or sees the problem I am really glad since my parents come home tomorrow and the computer down there needs to be up and running. So kind of making the night through trying different things while looking on help her.

I dont have another Pc to put the drives into so that falls out of question and after failing the ubuntu install the pc doesn't raid boot up anymore even after reversing the bios settings. I also installed ubuntu boot up helper so there might be a problem there as well.

Thx a lot Ubuntu Community for your help I am really running out on knowledge here xd.

---

### Post by TheFu on 2014-08-23
Clear the RAID bits on the both HDD partition tables and try again. It is a protection tool to prevent folks from thinking a HDD is empty when it is full of RAID bits and data. **gparted** can clear it - just boot off a liveCD or some other install disk.

Also - FakeRAID like most motherboards use is to be avoided, IMHO.  Use softwareRAID (mdadm) or a real, RAID card (something from LSI) if you need that level of performance. There is an Ubuntu "FakeRAID" howto on help.ubuntu.com somewhere. Google will find it, if that is your desire.  I've been using software RAID for many years.  Just migrated a few arrays last week from a 10.04 to a 14.04 install - it was 100%, completely, seamless. I just had to drop the UUIDs back into the fstab to get each mounted again.  The RAID devices were already created and ready. Linux software RAID is very flexible.

---

### Post by oldfred on 2014-08-23
Drives retain RAID meta-data, you have to remove that.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

