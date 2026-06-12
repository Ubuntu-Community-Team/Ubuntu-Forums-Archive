---
title: "Questions about duel booting Windows 7 and Ubuntu"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by jon60 on 2014-08-18
Hello, I'd like to install Ubuntu successfully this time, but keep Windows 7. On my hard drive, I have 440GB and was wondering the best size to partition. I won't be using Windows 7 for gaming or anything with large file sizes. Also, when I tried installing it, it said it couldn't detect Windows 7. How would I go about fixing that? Thanks a lot.

---

### Post by kansasnoob on 2014-08-18
It's good you asked. I can't help you with a work-around but you do need to be acutely aware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Other users know how to work around that safely, I know you can trust *oldfred* if he happens to stop by.

Sorry I can't be of more help. Just be patient and wait for someone to help rather than wiping out your Windows and losing data.

---

### Post by yancek on 2014-08-18
When you started the install did you select the manual (Something Else) option?  You should be able to create and select partitions from the installer.  You would need to know which partitions you have windows on and you can determine that by using:  sudo gparted to open gparted from a terminal or using:  sudo fdiks -l(Lower Case Letter L in the command).  Either will show which partitions you have windows on and how many you have.  You would need to either have a free partition or partitions or free/unallocated space which you should be able to find with either command.  Since we have no way of determining that, we can't give you any more specific advice.

---

### Post by oldfred on 2014-08-18
Make sure Windows is not hibernated.
Use Windows to shrink the NTFS partition and reboot immediately to clear the chkdsk needed flag. It will run chkdsk and update itself to its new size. But do not create any partitions with Windows.
And Windows 7 systems in BIOS boot mode almost always use all 4 primary partitions, so there is not an available partition for Linux. You have to backup & delete one partition, usually vendor tools and make a new extended partition. The extended counts as one primary but is in effect a container for as many logical partitions as you want. Windows only boots from primary partitions, but Ubuntu boots from logical without issue.
       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

    
Those are the main reasons it does not see Windows. If you still do not see Windows please add to this bug report and mention it also applies to Windows 7 and you are sure you cleared hibernation & chkdsk flags which do always prevent Linux from correctly seeing NTFS partitions. And you do not have all 4 primary partitions used.

       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Most Windows 7 systems are installed in BIOS boot mode even on some newer systems that will boot in UEFI mode. You need to install Ubuntu in the same boot mode as Windows.

Post this from the Ubuntu live installer in live mode, from the terminal:
sudo parted -l

---

### Post by ajgreeny on 2014-08-18
Windows 7 was mainly installed in BIOS machines with MBR, and not on machines using UEFI.

If yours is UEFI read [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") to make sure you understand that.  If it is an MBR machine there are plenty of sites with info on dual booting, including some of [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html) and this also gives a lot of detail on installing in general.

Points to remember.
[LIST=1]
[*]Always shrink your windows partitions using window's own disk management utility, never with gparted, and after shrinking, boot into windows to check all is well and to allow chkdisk to run. 
[*]Always use the "Something Else" or manual partitioning when you get to the partitioning stage of installing Ubuntu, and I suggest if you have two separate disks that you choose to put grub bootloader files on the same disk as Ubuntu, probably /dev/sdb, and not on the default which is the first disk /dev/sda, thus leaving Windows bootloader system untouched on the windows drive. 
[*]Make an ext4 partition of 20GB for root and set mountpoint /, and choose to format it. 
[*]If you want to hibernate the machine you must have a swap partition of at least the same size as your ram, but hibernation does not speed up boot a lot these days, so I am not sure it is worth it, and therefore I normally suggest a swap of 2 - 4GB. 
[*]I like to have a separate /home partition to easefuture distro upgrades, which is set as large as possible using all the available space.  This is an ext4 partition, with mountpoint /home. The first time you make it you should choose to format it.  Next time, at distro upgrade you will still have to choose to use it as ext4 and with mountpoint /home, but do not tick the format box or you will lose all the files in your home. 
[/LIST]

I hope this is some help, and good luck!

EDIT:-
Too slow again.  Oldfred is the "main man" for these sort of questions, so read and follow all his points and you will not go too far wrong.

---

### Post by jon60 on 2014-08-20
Sorry for the late reply. I've shruk the C drive so I have this:

[IMG]http://i.imgur.com/hCLDbaR.png?2[/IMG]


After setting the partitions, the installation fails - Errno 5. My hard disk is fine, I'm booting of a USB so I can't really see why the error is coming up.

---

### Post by oldfred on 2014-08-20
Not familiar with error number 5? From installer, gparted partitioner or something else?

Using Something Else with partitions created in advance with gparted should just work.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

for MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by jon60 on 2014-08-20
I've got it all up and running now, but thanks a lot for the help.

---

