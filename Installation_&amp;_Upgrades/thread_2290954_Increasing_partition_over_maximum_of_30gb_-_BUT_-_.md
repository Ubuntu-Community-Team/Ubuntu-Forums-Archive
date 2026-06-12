---
title: "Increasing partition over maximum of 30gb - BUT - when a whole drive was set aside"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by FIXXX on 2015-08-16
Hello!

As I'm trying to expand my use of Ubuntu looks like 30 Gb is not that much for more than casual use - so I initially set aside a small 120 GB hdd exclusively for Ubuntu.
But the installer allotted a maximum of 30, evidently. The explanations I've found as a rule explain how one adds more space - when you install on a windows-populated HDD.

But in my case it should be more simple. How would I go ahead about doing it. I keep coming back to Ubuntu 2-3 times per year and each time expands my knowledge, slow and steady :)

PS: Windows 10 is on its' own SSD, a storage HDD also separate and Ubuntu the same. In case it might be important. ):P

---

### Post by TheFu on 2015-08-16
Please post the output from both **sudo parted -l**
and 
**lsblk**

Until you get to 16TB, there aren't any limits on sizes with normal Linux file systems. Most support much more than that amount - Pb and Eb sizes are most commonly supported, but Zb is possible for some.
[https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

---

### Post by oldfred on 2015-08-17
There is a 30GB limit on wubi installs, but wubi is not supported anymore. But live installer for some reason still seems to have  a wubi.exe?

---

### Post by FIXXX on 2015-08-17
Model: ATA Hitachi HTS54161 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size   Type     File system  Flags
 1      368MB  120GB  119GB  primary  ntfs
 2      120GB  120GB  472MB  primary  ntfs         diag


Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size   Type     File system  Flags
 1      368MB  128GB  128GB  primary  ntfs         boot


Model: ATA SAMSUNG HD103SI (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot


NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   111G  0 part /host
&#9492;&#9472;sda2   8:2    0   450M  0 part 
sdb      8:16   0 119.2G  0 disk 
&#9492;&#9472;sdb1   8:17   0 118.9G  0 part 
sdc      8:32   0 931.5G  0 disk 
&#9492;&#9472;sdc1   8:33   0 931.5G  0 part 
loop0    7:0    0    29G  0 loop /

---

### Post by FIXXX on 2015-08-17
I used the tool that prepares a USB drive as installer. And used that.

---

### Post by oldfred on 2015-08-18
You are not showing any Linux partitions.
If you have Ubuntu then it is the now obsolete wubi install.
       Forums Staff recommendations on WUBI
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]http://ubuntuforums.org/showthread.php?t=2229766
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)


[/URL]

---

### Post by FIXXX on 2015-08-18
So essentially what you're implying that I should scrap this installation ? :eek:

---

### Post by howefield on 2015-08-18
> **FIXXX said:**
> So essentially what you're implying that I should scrap this installation ? :eek:

Look on the bright side, now you have a chance to do a real install  :)

If it is any consolation, Wubi was never intended for long term installations, it was only ever an easier way in to Ubuntu as it avoided the pitfalls of real partitioning. There are significant disadvantages in using it over a period of time.

---

### Post by oldfred on 2015-08-18
Since you have more than one drive, you need to use the slightly more advanced Something Else or disconnect other drives to only install to one drive.
You want to keep the Windows boot loader on the Windows drive and only have grub on the Ubuntu drive. But only in Something Else can you also choose which drive to install grub2's boot loader into.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
      [/URL]
 Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]
[/URL]

---

### Post by FIXXX on 2015-08-18
That's what I hate with Linux - no tl;dr. :roll:
I seem to remember that I disabled other HDDs last time i installed Ubuntu so i'll probably go that route.

---

### Post by FIXXX on 2015-08-19
An update:
After installing on the single HDD (others disconnected) it stopped showing the windows boot menu with the selector of Windows and Ubuntu. Had to use F12 and manually select the Windows drive.
Tried repairing the installation but no luck. And alongside this bad luck - had the bright idea to select full drive encryption not knowing how hard it is to undo.
So had to scrap the whole thing. Once again Ubuntu proved to be too cumbersome for my basic level of skills :( Next year then.

---

