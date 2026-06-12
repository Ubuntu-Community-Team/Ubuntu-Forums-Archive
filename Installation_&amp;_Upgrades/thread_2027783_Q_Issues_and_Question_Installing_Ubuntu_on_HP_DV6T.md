---
title: "Q: Issues and Question Installing Ubuntu on HP DV6T-7000"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by monkeychef on 2012-07-17
Hello everyone,

I posted this in the laptop thread as well, as I am not completely sure where to post this specific question.

I just got the new HP DV6t-7000, and I really want to dual boot Win7 and Ubuntu 12.04. Here are some of the hurdles that I have to go through:

Disable Intel RST as there is a 32gb cache mSSD drive along with a 1tb HD

Figure out how to partition correctly so that I keep necessary partitions while also creating a partition that I can use for Ubuntu

On the HP, there are 4 stock partitions that come out of the box which include the Boot, OS, Recovery, and HP Tools. I shrunk OS and created a 100gb drive I named Linux. I later booted gParted and converted the Linux drive over to Ext4 so that I could install Ubuntu onto it. However, as noted in my other thread ([http://ubuntuforums.org/showthread.php?t=2015035](http://ubuntuforums.org/showthread.php?t=2015035)) I am very confused about which partition is which. I am very concerned about deleting something that I really don't want to delete, but at the same time I am very confused as to why my main OS partition is hiding my Linux partition when I attempt to install the OS.

If anyone needs any more information, please reply to this thread or send me a PM. Thank you so much for your help guys.

---

### Post by monkeychef on 2012-07-17
This is my last post for the night.

Until someone responds, I am going to stop trying to install Ubuntu.

Because of this, I went to try and reactivate Intel RST, but now I'm having an issue with the disk not being accelerated. Maybe it takes time to cache, I don't totally know.

I'm thinking about just recovering from a backup and moving forward from there.

---

### Post by UltimateCat on 2012-07-17
I don't know it all but I'll share with you what I do know.

If your trying to install from a cd during the process of installation you should be prompted for the Option to manipulate all partitions by editing them, delete or select already existing. 
 You can replace your existing Operating System
  Install alongside ( this is what I did as I am dual booted with Windows XP)
or do your own thing manually-

These websites should be helpful:

[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
[http://help.ubuntu.com](http://help.ubuntu.com)

Also; Only install packages officially supported for your version of Ubuntu and Read all of the documentation:wink:

Hope this helps answer some of your questions

---

### Post by mastablasta on 2012-07-17
if the HP tools partition is primary partition (which it probably is) it will cause you problem as you won't be able to install any additional OS next to current OS install. Not even windows 8
 
so you need to back it up delete it and create a new non-primary (extended) partition there instead.
 
linux marks parition on same disk like so: 
/sda1 = first partition
/sda2= second partition
...
an easy way to see where you are instlling is to see the disk size. if you set 30 GB for Ubuntu look for a partition with 30 GB.
 
i can't help you with hybrid disk as i don't know much about it.

---

### Post by monkeychef on 2012-07-17
Alright, so here is an update.

Because I disabled Intel RST and I added a 5th partition to my hard drive, it is no longer in a RAID 0 array. Because of this, I can not re-activate Intel RST. This will be my next course of action:
[LIST=1]
[*]Backup Files (almost dones)
[*]Restore a recovery image from a few days ago with RST intact and no partitions edited
[/LIST]

From there, I will attempt to install Ubuntu this way:
[LIST=1]
[*]Configure Intel RST to use only 18.6GB of mSSD (only other configuration available). This leaves about 11GB for Ubuntu.
[*]Activate 11GB drive, but will not touch until booted into Ubuntu
[*]Create new partition table and make Ext4 partition on 11gb drive
[*]Intall Ubuntu to 11gb drive
[/LIST]

Once this is done, I hope that I will have Ubuntu running from the mSSD. I do have a few more questions:
[LIST]
[*]Is there any way to keep the 11gb for just the OS, and move the rest of the data to another source (say a 16gb SD card in the laptop)?
[*]Does anyone know if this will work (lol)?
[/LIST]

Thanks for the feedback so far guys. You all rock.

---

### Post by monkeychef on 2012-07-18
Alright, I've just about given up. I don't have a clue what to do at this point as I am at a loss.

---

### Post by jwb84 on 2012-07-31
I tried to install Ubuntu on the same type PC.  The Ver. 10.10 works, but there is no audio.  The Ver. 11.xx crashes in the middle of the installation.

---

### Post by oldfred on 2012-07-31
If you create partitions with Windows and already have the 4 primary partitions, it will convert to dynamic from basic partitions. Dynamic does not work with Linux and does not always  work in Windows for repairs.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by Just Work on 2012-11-14
I have the same (or close enough) computer with the same four partitions, and the same set of headaches. To clarify-- with the four existing HP-made partitions, I can't make another partition to put on OS on?

Edit: For what it's worth, I have a dv6 with four partitions existing on it. The machine has a hybrid hard drive. Between the partitions and the HDD, I've had no end to trouble installing an OS alongside Windows 7. Which problem (or both) is the one that needs to be fixed for me to install any other OS?

---

