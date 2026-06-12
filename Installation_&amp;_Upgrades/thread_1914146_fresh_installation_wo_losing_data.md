---
title: "fresh installation w/o losing data"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by srtraveler on 2012-01-23
I have searched without finding specific or detailed answers or references (I am willing to find the info if I can get some direction). I want to buy a new computer with Ubuntu 12.04 installed ~3 weeks after its release. I am using 10.04 LTS currently. I want to transfer all my programs and their data files from my external HD to the HD on my new computer. A problem for instance is that not everything resides in my current Home folder and it is not always clear where that might be. Is there an article or a chapter in a manual or a place on the internet that gives instructions for a step by step copy or mass backup to an ext HD so that retrieval and reinstallation of programs and data will be relatively secure? Surely this is a problem that thousands of users have encountered. Do I need an OS partition and another partition on my new computer and then copy everything from the backup to the program and data partition? Help will be appreciated. Please let me know if this is not clear.

---

### Post by varunendra on 2012-01-24
I'm not sure, but just believe that-

If you upgrade to a newer OS/kernel from a much older one, most of the packages would be upgraded anyway. As such, the download size would be almost same as reinstalling them from scratch.


Having said that, here's what you can do (I'd recommend you do it when 12.04 is officially launched)-

**A) _Imaging Partitions_:** Although you can directly copy disk/partitions from one to another drive, imaging it would serve as a safe backup in case something goes wrong:

[LIST=1]
[*]Download clonezilla live cd iso and burn it to a cd ([see how]("https://help.ubuntu.com/community/BurningIsoHowto"))
[*]Boot from it and create images of all your linux partitions ([see how]("http://www.dedoimedo.com/computers/free_imaging_software.html"))
[*]Save this image folder to a secure place, preferably on an external drive.
[/LIST]


**B) _Cloning Hard disk_:**

 

[LIST=1]
[*]Make sure both the new and the older (on which 10.04 is currently installed) drives are connected to the new computer.
[*]Boot the new computer with Clonezilla live cd.
[*]After choosing defaults in language and kemap screens, choose "**device-device**" option this time (as opposed to default "device-image" option which is for imaging or restoring from image).
[*]Select defaults in the next couple of screens until you get the "source disk" selection menu. Choose the 10.04 disk as "**source**" (make sure you identify it correctly)
[*]The newer disk will automatically get selected as "target" in the next screen
[*]Go with the defaults in the next screens, answer 'y' wherever asked, and let the 'cloning' start and finish. (from safety's point of view, it will ask you two or three times before starting actual cloning. Funny, but intelligent! :))
[/LIST]
[***Important: **If any of the source partitions are **ntfs **which are "****not ******clean**" (improperly shutdown or have other errors), the cloning _may fail_. In that case, you will need to either fix the errors in windows by using "chkdsk" and properly shut it down this time, or use "**Advanced mode**" in clonezilla to "**Ignore**" such errors*.]



**C) _Upgrade_:**

[LIST=1]
[*]Download live cd of 12.04 (same architecture as 10.04 is, that is 32-bit or 64-bit)
[*]Burn the iso to a cd and boot with the live cd.
[*]Choose "install"
[*]The partition selection menu would present the option to "Upgrade 10.04 to 12.04". Choose that.
[*]Proceed with further installation steps till "finish".
[*]Reboot from hard disk, and verify if the upgrade is stable.
[/LIST]
This was just one of the many other possible ways to move the installation. But I think this was the most straight-forward for moving 'everything' to a new computer in the safest way.

---

### Post by srtraveler on 2012-01-24
Thanks for the detailed response. Here is another help link and a marvelous tool I didn't know existed until recently--
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#How_to_find_out_which_kernel_you_are_using](http://ubuntuguide.org/wiki/Ubuntu:Lucid#How_to_find_out_which_kernel_you_are_using)
Scroll down until you see
Reinstalling applications after a fresh install--very clear to me. Haven't tried it yet.

---

### Post by oldfred on 2012-01-25
I regularly use dpkg to reinstall all my applications on a new clean install, including testing of the next release. But you may want to manually review file, it is just a text file. I found I was still reinstalling python2.5. Now they have changed from OpenOffice to LibreOffice and you may not want both, possibly others also.

My backup for my home system is just a new clean install and backup of what I think is the important data.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh - I modified this script for my use.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat

---

### Post by varunendra on 2012-01-25
> **oldfred said:**
> I regularly use dpkg
..
..
<stuff>
<stuff>
<stuff>
..
..
..
..
<stuff>
<stuff>
..
..
Other applications if data not separate
apache, any sqldb, tomcat
Wow!! And I thought you speak English only! :P

---

