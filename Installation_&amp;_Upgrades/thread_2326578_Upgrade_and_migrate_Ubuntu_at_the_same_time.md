---
title: "Upgrade and migrate Ubuntu at the same time"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by Stuart_Burnley on 2016-06-02
I have Ubuntu 14.04 on an HDD and would like to have the Operating System on my new SSD. My SSD is 256Gb and is split currently with Windows 7 - 121GB, and free space - 116Gb.

Can I use the upgrade process from 14.04 to 16.04 to get  16.04 running on the SSD? 

I would like to end up with 16.04 running on the SSD, my "home" folder (and therefore all my files, music, videos etc) where it is currently on the HDD, Linux swap folder where it is currently on the HDD, and all my installed apps continuing to run after the upgrade. This particularly includes mythtv, which I would prefer not to have to setup again.

My thinking is that I would select manual partitioning ("Something Else") from the upgrade window, choose unallocated space on the SSD to install 16.04, but do not create a /home folder or /swap partition. 

Is it straightforward, or would there be any snags to watch out for?

thanks, Stuart

---

### Post by oldfred on 2016-06-02
I do exactly that, but typically have two Ubuntu installs on SSD and more on HDD. So I keep /home inside / (root) and only sometimes restore my backup of /home into on of the installs.
But all my data is in /mnt/data on HDD and I can easily link that into each install, so no matter what I boot I have all the same data. 
When I still had XP I had two data partitions, one NTFS for data I wanted to share with Windows, including my Firefox & Thunderbird profiles.

UEFI or BIOS? Most Windows installs were BIOS/MBR, but a few were UEFI.

If you have a long list of installed apps, you want to export that list so you can reimport it. All your user settings for apps are in /home. But if you made system wide settings or databases (maybe myth, do not know), may also be in /etc and you want to have backup of that system folder. 

       discussion of alternatives/strategy backups
[URL="https://help.ubuntu.com/community/BackupYourSystem"]https://help.ubuntu.com/community/BackupYourSystem
[/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) 

[URL="https://help.ubuntu.com/community/BackupYourSystem"]
[/URL] While I "backup" copy some data from SSD to HDD, I do not really consider that backup as changes are not archived. My copies of most essential data to DVD or flash drives are my backups.

---

### Post by Stuart_Burnley on 2016-06-04
Thanks for the response and the links.

Stuart

---

