---
title: "How to Install Ubuntu Beside Windows 7 on Raid 0 Config."
date: 2014-03-26
forum: Installation &amp; Upgrades
---

### Post by Votlon on 2014-03-26
So basicly, I have the Alienware 18 laptop, which is a wonderful laptop btw<3 but its been a pain in my ass for the last 20 hours trying to figure out how to install linux on it. 

Here is a pic of my partitions in windows:[URL="http://www.evernote.com/shard/s406/sh/d2fef410-9d7d-42eb-88b5-ebb9b29d5f68/cce66eccf2aa2441b351c0a701768f93"]
http://www.evernote.com/shard/s406/sh/d2fef410-9d7d-42eb-88b5-ebb9b29d5f68/cce66eccf2aa2441b351c0a701768f93[/URL]

Here is a pic of my Speccy report on my hard drives in windows:
[http://www.evernote.com/shard/s406/sh/9083b42a-4b14-40a1-bd89-a6a9cf132a38/84a0668d093f3e0cff5de0260a2bca3d](http://www.evernote.com/shard/s406/sh/9083b42a-4b14-40a1-bd89-a6a9cf132a38/84a0668d093f3e0cff5de0260a2bca3d)

All I really want to do is get Ubuntu on my free spaced partition, but i have tried a plethora of retarded un-experienced crap that has resulted in me re-installing windows twice today. 8-)

I'm going to boot to ubuntu then take a picture of what the partitions look like in the installer, because that's what really keeps throwing me off.


**I have a 10gb hard drive as well on my system but its for a hard drive cache.

---

### Post by Votlon on 2014-03-26
This is when i started crapping myself.

Top of the list:
[http://www.evernote.com/shard/s406/sh/e2635aca-83c4-4292-9155-6e7abce9a687/b224e5fcaa88dc68318096a297c3d03a](http://www.evernote.com/shard/s406/sh/e2635aca-83c4-4292-9155-6e7abce9a687/b224e5fcaa88dc68318096a297c3d03a)

Middle of the list:
[http://www.evernote.com/shard/s406/sh/69af961b-07bb-493e-b245-a06363e230a5/c7e1d7cc2bc8a4e4f2ab8604f8722471](http://www.evernote.com/shard/s406/sh/69af961b-07bb-493e-b245-a06363e230a5/c7e1d7cc2bc8a4e4f2ab8604f8722471)

Bottom of the list:
[http://www.evernote.com/shard/s406/sh/31f15984-2914-4ac3-a6da-8625ccea1913/c6bbd0efeef73ab38016c7c39050e300](http://www.evernote.com/shard/s406/sh/31f15984-2914-4ac3-a6da-8625ccea1913/c6bbd0efeef73ab38016c7c39050e300)

Is it even possible to get Ubuntu on my system?

---

### Post by oldfred on 2014-03-27
What version of Ubuntu?
The desktop installer did not include RAID drivers. But it looks like you now see them.
Did you install the RAID drivers?
sudo apt-get install mdadm

With 12.04 you have to use alternative installer or server installer to use RAID or LVM.
They then said they were discontinuing separate alternative installer and would add RAID & LVM to desktop. And newest versions do offer LVM, but not sure about RAID.
You also have to install grub to the root of the RAID not the default sda.

 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

---

### Post by Votlon on 2014-03-27
Sorry I should have included that, I was using 12.04 Ubuntu Dekstop 64 bit. And I did not download any drivers, to download drivers would I have to boot to the live cd and install the drivers and os from there?

---

### Post by oldfred on 2014-03-27
If you want 12.04 download the alternative installer. It is text based but otherwise looks and works similar to gui based installer. And you get the same install.

This is not a RAID install, but shows text based screens.
 Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

I just noticed you mention RAID 0. I might consider breaking RAID and just have two drives. Then you can use part of second drive for Windows backups. And have Ubuntu on separate drive. And use part of Windows drive for Ubuntu backups.
I consider backups a lot more important than the bit of speed you get from RAID 0. And if you want speed add a SSD.

       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by Votlon on 2014-03-27
I love that idea of splitting the raid 0 i didn't even think about that. I need to check my dell support warranty though, because i have the accidental support which is so wonderful. :p I've broke my alien 18 three times(once i smashed in the whole screen from a nasty fall) and they have sent me a whole new laptop every time! I know that installing my own hard drives breaks that warranty so i don't know if changing their factory configuration from raid 0 will also break it.

Thank your for the help oldfred :) I'll post once I've figured out what i'm going to try.

---

### Post by oldfred on 2014-03-27
I have seen one or two posts where a user said he split the RAID. Not sure of details as I have never done it.
I suggest good backups whatever you decide to do.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

