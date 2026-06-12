---
title: "Ubuntu 18.04 on SSD, how to make /home on HDD"
date: 2018-05-31
forum: Installation &amp; Upgrades
---

### Post by johnspeedster on 2018-05-31
Just bought a Dell Inspiron 5577-5858 i5, 7300HQ 1TB HDD laptop and had a 250GB Samsung SSD added. Windows 10 is on the HDD and I have installed Ubuntu 18.04 on the SSD. I want to remove/delete Windows and make the HDD /home. Can anyone explain please or point me to clear instructions. Do I need to format the HDD or just change partitions using Gparted? Will changing partitions on sdb alter the Ubuntu installation? There is nothing on the HDD that I want to keep.
Thanks in anticipation...

---

### Post by oldfred on 2018-05-31
Often better to keep Windows, you paid for it. And many users come back and want to reinstall Windows as they have one app or game they must have that only runs in Windows. Or later want to sell system and then it needs Windows.
 Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
   How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
[http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/](http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/) 

For /home you will need an ext4 partition. Use Windows to shrink the NTFS partition if keeping it, leaving some space. Then use gparted to create a new ext4 partition, copy all of /home to that partition and remount using fstab to use new /home partition. 
Details:
      To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Bit more advanced is a data partition keeping /home inside /, but having all your data in a separate partition and linked back into /home. I do this since I want to have more than one Ubuntu install,just to test or experiment with. Then I do not have to worry about corrupting my main working install.

The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by johnspeedster on 2018-06-01
Brilliant. Many thanks for such a clear and well described answer. I will keep Windows as you suggest - plenty of room!

---

