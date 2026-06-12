---
title: "Ubuntu installation dual-boot help?"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by ispeaklatin on 2012-03-28
I tried installing Ubuntu on my Windows 7 machine and I want to install it so that I can dual-boot, but when I get to that page in the installation window, it only has the options to format my hard-drive and start fresh with Ubuntu or the something else option. There's no way I am going to format my hard-drive and I'm not advanced enough with computer to know what I'm doing in the "Try something else..." menu. Please help!?

---

### Post by Dngrsone on 2012-03-28
You need to make room for your Ubuntu installation on your hard drive.

First, make a backup of your data; and if you haven't created a restore disc, then do that as well.  That way, if something catastrophic happens, you can fix things after.

In Windows 7, go to Control Panel, Administrative Tools, Disk Management.  Right-click the drive you want to shrink (most likely this is the Windows drive, C: )

This will make an unformatted partition for you to use.

When you boot the Ubuntu CD, then you will want to tell it to use the unformatted partition to install the OS to.

[Here](https://help.ubuntu.com/community/WindowsDualBoot) is the basic instruction for installing Ubuntu in a dual-boot configuration.

[Here](http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html) is another, with fancy pictures.

I suggest you read through the tutorials before doing anything.

---

### Post by oldfred on 2012-03-29
Many Windows 7 systems have all four primary partitions that you can have used. You have to backup and delete one. And that one partition can become an extended partition to hold many logical partitions. Windows only boots from a primary partition, but Ubuntu works just fine from logical partitions.

Whatever you do do not create partitions in Windows as it converts from basic to dynamic which does not work with Linux.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

