---
title: "Partioning Hard Drive for new install"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by maplewood on 2012-10-17
I've got a laptop with lots of Windows issues so I decided to switch/add Ubuntu.

I figure that I should "date" ubuntu before I give XP its final walking papers. (This is all new to me.)

The Installer asks if I want to erase everything or do Something Else.

The screen that comes up for "Something Else" has these options:

/dev/sda1/   Fat 16    Size=41mb  Used=33mb
/dev/sda2    NTFS      159998MB   Used  Unknown


There are buttons for
[LIST]
[*]New Partition Table
[*]Add
[*]Change
[*]Delete 
[*]Revert
[/LIST]

And a drop down list for "Device for Bootloader installation with:
[LIST]
[*]/dev/sdb
[*]ATA Toshiba (160GB)
[*]/dev/sda1
[*]dev/sda2/Windows NT/XP
[/LIST]

Ok, I know I don't want to overwrite the XP partition but other than that I'm quite clueless.

This laptop will be mostly used for browsing, email, Google Drive, etc.  It will also (eventually) be on Windows network with a Win 7 and a XP machine.  Very little needs to be stored locally.

(BTW, I saw one thread with a screen shot that had a choice of Install alongside Windows but that option was not part of this installer)

Guidance?

---

### Post by jerrrys on 2012-10-17
It looks to me that you have 4 primary partitions and thats the max you can have on one hdd.
If this is the case, that is why you are not given the option to install side-by-side.
Can you verify this?

---

### Post by maplewood on 2012-10-17
Thanks for this help.

Not sure how I have four. 

I tried a WUBI install from Windows and that failed so maybe one is from that.

How do I check the number of partitions at this point?

I suspect that I could use one of the existing for the install -- but which one?

---

### Post by oldfred on 2012-10-17
To see partitions, use terminal on liveCD and run either or both of these:

sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print


If Windows needs a chkdsk then Ubuntu may not mount it and cause issues. It used to not even show drive as I had XP on a separate drive and gparted would not even show drive. But XP seemed to work. Ran chkdsk, gparted then saw drive and XP booted a bit faster.

---

### Post by maplewood on 2012-10-17
I ran chkdsk /r after the WUBI install failed and it seem to think the drive was okay.

To help you understand how foreign this is to me:  What or where is LiveCD?

I am installing from a USB as the DVD drive is flaky.

---

### Post by jerrrys on 2012-10-17
I have not ran windows for many years and a little hard press to tell you how.  So here's a link for windows that may help.

[http://www.google.com/search?q=list+partitions+windows+xp&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=list+partitions+windows+xp&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

If you want to do it in linux you can use the ubuntu live CD.  Use the option to try without installing.  Then [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo fdisk -[B][COLOR=Blue]l

And that's a lower case L

[COLOR=Black]EDIT:  oldfred has you covered[/COLOR]
[COLOR=Black] [/COLOR][/COLOR][/B]

---

### Post by maplewood on 2012-10-17
thanks  (so Terminal is invoked with CTL ALT T)

The sudo fdisk -l
Tells me  a lot of things I don't understand but among them seem to be:

-  dev/sda has 160GB
SDA1 starts at 63 and ends at 80324  (Dell System)
SDA2 starts at 81920 and ends at 156248920 (HPFS/NFTS/exFAT

SDB is 1055 MB
/dev/sdb1 starts at 32 and ends at 2060799   W95 FAT32 (LBA)

Whatever the hell all that means.

---

### Post by oldfred on 2012-10-17
You have a liveUSB or a working Ubuntu that runs on a CD or USB and is also an installer.

Kinda wanted you to copy & paste the terminal output like this. You can also copy & paste the commands we post, that way there is no confusion on letters like l, 1, I which depending on font used may all look the same.

```
fred@fred-Precise:~$ sudo fdisk -lu
[sudo] password for fred: 

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa51fa51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   115330634    57665286    7  HPFS/NTFS/exFAT
/dev/sda2       156296385   312576704    78140160   83  Linux
/dev/sda4       115330635   156296384    20482875    b  W95 FAT32

Partition table entries are not in disk order



```

If text is long or formated you should use code tags. You highlight like copy, but then in the edit panel above your message click on # and it will auto add code tags.

---

### Post by maplewood on 2012-10-17
Okay, so it is very cool that I can actually run Ubuntu off the USB drive.  (Try what with Windoze!)

(I had been install with one machine and following this thread on another)

The output of the sudo command is:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920   312579759   156248920    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1055 MB, 1055129600 bytes
2 heads, 63 sectors/track, 16355 cylinders, total 2060800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00146715

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     2060799     1030384    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ c

---

### Post by oldfred on 2012-10-17
It is only two partitions. With Windows 7 there are often hidden partitions and vendor partitions and they use all 4 primary partitions.

With XP, use gparted to shrink it, If newer Windows always use the Windows partitioning tools to shrink Windows. Do not shrink too much as NTFS really likes 30% free space to run well. Houseclean and defrag before shrinking as the shrink will be faster if there is less data at end of partition. And after shrinking reboot XP a couple of times so it can run chkdsk and update its new size.

Backups are always a good idea with any system change.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)


You can create partitions as part of the install easily now, or in advance, but then you have to use Something else to use existing partitions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

 I was still running XP for 5 years before just this year I managed to  stop using the last application on it.  The equivalent in Ubuntu is not as good, but now is good enough for me.

---

### Post by maplewood on 2012-10-18
> **oldfred said:**
> It is only two partitions. With Windows 7 there are often hidden partitions and vendor partitions and they use all 4 primary partitions.

With XP, use gparted to shrink it, If newer Windows always use the Windows partitioning tools to shrink Windows. Do not shrink too much as NTFS really likes 30% free space to run well. Houseclean and defrag before shrinking as the shrink will be faster if there is less data at end of partition. And after shrinking reboot XP a couple of times so it can run chkdsk and update its new size.

Backups are always a good idea with any system change.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)


You can create partitions as part of the install easily now, or in advance, but then you have to use Something else to use existing partitions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

 I was still running XP for 5 years before just this year I managed to  stop using the last application on it.  The equivalent in Ubuntu is not as good, but now is good enough for me.

Thanks for that comprehensive advice.

I think this means that I can
[LIST]
[*]shrink my current Windows partition (it's pretty big now)
[*]I should then divide the new free space into two or three partitions so that Ubuntu is happiest
[*]Do this before I install Ubuntu
[/LIST]

I noted the second two bullets as I am not clear as to what you mean in bullets 1,2,3 "Ubuntu Partitions." 

Ideally I would be able to simply shrink the current Windows partition and then start the Ubuntu installer. At that point the Installer would ask me if I want a dual boot (yes) and let it go from there.  Perhaps the installer will add any additional "sub" partitions.

Also, could I use something like Windows Partition Wizard to make the change?  (That utility confirms your diagnosis of only two partitions).  The only question is whether I can or should learn to use Gpart or can I rely on the more familiar Windows tool.

---

### Post by oldfred on 2012-10-18
Use Windows tools for Windows and Linux tools for Linux. 

There are issues with Windows 7 MMC creating partitions. It is good for shrinking the Windows c: drive, but converts to a proprietary dynamic partitioning scheme which does not work with Linux nor some Windows repair tools. 

Best to learn gparted. The manual installer is almost identical to gparted.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

If just starting and use the auto install options you get the default of / (root) and swap. That is fine but I found the shared NTFS partition is very useful and best to plan for that right away. 

Then when upgrading many of us like to do clean installs. You can and should be anyway backup /home and then reinstall that with your data. If you do upgrade in place all you data is saved but over time you do build up cruft and need a through housecleaning. (Same for Windows). New clean install is an auto houseclean and with Ubuntu a little planning makes it pretty quick, where in Windows you need so many reboots and housecleaning & reinstalling stuff it can be a day project.But a new install is a bit easier with a separate /home. You can move all the /home files  later to a separate partition if desired.

---

### Post by maplewood on 2012-10-18
thanks for all this help.

One of the reasons I went to Ubuntu was for the opportunity to learn something new.  Which was fun.

I also learned to read the default boot screens more carefully. 
Earlier I had tried to install Ubuntu but it seem to have failed (I got a blue screen suggesting Chkdsk).

Today when I rebooted the device I noticed that Ubuntu was one of the choices (along with Windows and Install Windows.  For some reason the device is defaulting to the Install option and since there is no CD available it throws the blue screen).

So that original installed seems to have worked (which may have explained the multiple partition listed in the installation option).

Live and learn.  Now to learn about adjust partition sizes with Gpart.

Again, thanks for all this great help.

---

