---
title: "Installing dual-boot Ubuntu"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by TimmyK. on 2011-06-17
Hi, when you put the Ubuntu install DVD in, it gives you the options to erase everything on your disk or partition it. If you want a dual-boot, do you just partition it and install? Or do you need to partition it from the first operating system or do anything before the Ubuntu install DVD? Thank you for your time.

---

### Post by tubunu on 2011-06-17
If you want to dual boot, select manual partitioning and assign your Windows partition to /windows and create three separate partitions for your Ubuntu, i.e. root (assign it to / ), home (assign it to /home - it's useful to have a separate /home partition separate from the system), and swap (assign it to /swap).

---

### Post by goldshirt9 on 2011-06-17
[COLOR=Red]you use the partition option.[/COLOR] then tell ubuntu how much hdd space you want it to use.
if you format then all of your original operating system will disappear .

google for tutorials , there are plenty.

back up all important info first though. 


always helps to defrag windows first though ( if its windows you use)

---

### Post by oldfred on 2011-06-17
If it is not giving an install alongside then you may have all 4 primary partitions used? Windows 7 often is set up to use all 4.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by TimmyK. on 2011-06-17
So you don't have to do anything on the original OS, just with Ubuntu install DVD? So much easier than Windows! Thanks guys.

---

### Post by nzjethro on 2011-06-17
> **TimmyK. said:**
> So you don't have to do anything on the original OS, just with Ubuntu install DVD? So much easier than Windows! Thanks guys.

That's correct. If you don't want to, you don't have to. If you'd like to clear up more space for Ubuntu though, it is recommended that you defragment your Windows (if that's what you dual boot with) drive a couple of times, just to free up your space. Also, if you feel up to it, you can specify your own partitions and create partitions yourself during the installation process, but if you just want to dual boot and not stress, it'll do it for you.

---

### Post by TimmyK. on 2011-06-17
Well, I've got something like 150 GB of free space, so I'm in no shortage. And I want something more than 20 GB for Ubuntu, so will manually partitioning it do the same thing but just with the space you specify? Either way you need to do no partitioning from the OS already on there? And can I view documents from the other OS without rebooting?

---

### Post by oldfred on 2011-06-17
I prefer to partition as then I have control over sizes and can add a /home. If dual booting from windows you should add a NTFS partition for shared data. Ubuntu can read the windows install, but writing alot of data can give windows fits and windows cannot read Linux partiitions. A shared NTFS is best.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).

---

