---
title: "winxp dual boot: allocate drive space strategy"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by Dondermans on 2010-10-21
Hello all,

Having tried a Wubi-version of Ubuntu 10.04 in combination with Windows XP, I have reached the conclusion that I would like to keep Ubuntu as my main operating system. Windows XP should remain for the time being, because I would like to play a game once in a while. 

Therefore I would like to install Ubuntu 10.10 alongside Windows XP. I have made a backup and installed Windows XP+SP3 using a streamlined DVD that I created a couple of months ago. Then I allowed Windows Update to download the updates which were released since I created the streamlined DVD.

On my previous install (Windows XP + Ubuntu 10.04 in Wubi), I defined a NTFS-partition of 25GB. That proved to be too small for practical use. Having streamlined the installation I could not define the NTFS-partition size in the Windows installer hence I used Partition Magic in Windows XP to resize the NTFS-partition to 60GB. I deleted the partition on the remainder of disk 1 and intend to allocate it using the Ubuntu 10.10 installer:

[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/partitionmagicwinxp_v2.jpg[/IMG]
Illustration 1: Oversight of installed disks. Disk 2 is used for storage and backup purposes.

Once Partiton Magic finished, I ran chkdsk with both options enabled, to ensure the drive is healthy:

[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/chkdskwinxp_c.jpg[/IMG]
Illustration 2: Chkdsk ran completely without hickups when I rebooted the system.

I intend to install Ubuntu 10.10 using a USB Pendrive. I have read the following guides:
[COLOR=RoyalBlue]
[[COLOR=blue]WindowsDualBoot[/COLOR]]("https://help.ubuntu.com/community/WindowsDualBoot") [COLOR=RoyalBlue]
[[COLOR=blue]Ubuntu 10.10 manual disk partitioning guide[/COLOR]]("http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/2/")[/COLOR]
[/COLOR]  
The WindowsDualBoot guide does not facilitate a seperate partition for my /home directory, while the Ubuntu 10.10 manual disk partitioning guide does not account for a Windows XP installation. I have tried following the second guide verbatim, but I cannot since the traditional disk partitioning system only allows for 4 primary partitions.

I would like to allocate a seperate partition for my /home drive to make sure that I can rescue my data (besides employing a backup strategy). I do not suppose I need a seperate partition for /boot, as suggested in the 'manual disk partitioning guide'. I do not mind having to reinstall Ubuntu, as long as my personal data is safe in the event Ubuntu won't boot for whatever reason (the reason most likely being my actions :)). I value my e-mail and bookmarks as 'most important' e.g. my /home/.thunderbird and /home/.mozilla folder.

Hence I devised the following solution:

[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/partition1_c.jpg[/IMG]
Illustration 3: 20GB for the root file system.

[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/partition2_c.jpg[/IMG]
Illustration 4: 5GB for the swap file (I have got 4GB RAM).

[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/partition3_c.jpg[/IMG]
Illustration 5: The remainder is to be allocated to the /home directory (an 1 TB External drive allows for additional storage and serves backup purposes).

[B]Question: Would you please comment on the allocate drive space strategy described above? I am particularly interested in pros and cons of this strategy and how it can be improved. It is essentially what is suggested in the Ubuntu 10.10 manual disk partitioning guide without a partition for the /boot directory.

Thanks in advance for any insight!
[/B]

---

### Post by jerrrys on 2010-10-21
ok, here is my 2 cents worth or better put, i like easy...

so i would just go ahead and install ubuntu on that 90 gig of free space (side by side install).  don't need to make a swap partition, the install will auto do that for you; it won't be 5 gig, but you really don't need that much.  as for a home partition; i would not bother with that. sure; it can be done, but why not just backup/sync your home folder to the second drive and be done with the install.  like i said, i like easy...:)

about forgot...leave the free space just as is and the install will give you the option to install there.  if you want to save some of that free space for whatever, go ahead and format to ext3 and the install will leave it alone. am i making any cents. :)

---

### Post by Dondermans on 2010-10-22
> **jerrrys said:**
> ok, here is my 2 cents worth or better put, i like easy...

so i would just go ahead and install ubuntu on that 90 gig of free space (side by side install).  don't need to make a swap partition, the install will auto do that for you; it won't be 5 gig, but you really don't need that much.  as for a home partition; i would not bother with that. sure; it can be done, but why not just backup/sync your home folder to the second drive and be done with the install.  like i said, i like easy...:)

about forgot...leave the free space just as is and the install will give you the option to install there.  if you want to save some of that free space for whatever, go ahead and format to ext3 and the install will leave it alone. am i making any cents. :)

Thank you for your reply. The reason why I am looking into creating a seperate partition for my /home directory is that I am still learning my way around in Ubuntu and I would benefit from what I perceive to be 'additional security' when it comes to my personal data. Also, I do occassionly forget to make a backup and do need to think out a backup strategy (particularly for my e-mail and bookmarks). 

There's no need for free space on my HDD, as I have got an external drive and I am currently not considering using more than two operating systems.

---

### Post by jerrrys on 2010-10-22
each to his/her own.  thats what makes linux so great.  for idot free backup i like rsync (grsync) and worthy mention is luckybackup.  i dont use the option, but encrypted backup is available. and last, if you haven't already been there... 

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=seperate+home+directory&as_qdr=all&sa=Google+Search&lang=en#1095](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=seperate+home+directory&as_qdr=all&sa=Google+Search&lang=en#1095)

---

### Post by Dondermans on 2010-10-24
> **jerrrys said:**
> each to his/her own.  thats what makes linux so great.  for idot free backup i like rsync (grsync) and worthy mention is luckybackup.  i dont use the option, but encrypted backup is available. and last, if you haven't already been there... 

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=seperate+home+directory&as_qdr=all&sa=Google+Search&lang=en#1095](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=seperate+home+directory&as_qdr=all&sa=Google+Search&lang=en#1095)

Thank you for your suggestions and the link to googlubuntu! I quite like the Ubuntu concept, which appears prominently on these forums.

---

### Post by oldfred on 2010-10-24
If you are using both windows & Ubuntu I like to create a separate /shared NTFS partition for data that you may want in either system. I put my firefox and Thunderbird profiles in the shared. Originally we were mostly windows and while booted in Ubuntu to learn it, my wife wanted to check email or get on the Internet and wanted the same bookmarks. So I created the NTFS partition and email & firefox were then identical in both.

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by Dondermans on 2010-10-24
> **oldfred said:**
> If you are using both windows & Ubuntu I like to create a separate /shared NTFS partition for data that you may want in either system. I put my firefox and Thunderbird profiles in the shared. Originally we were mostly windows and while booted in Ubuntu to learn it, my wife wanted to check email or get on the Internet and wanted the same bookmarks. So I created the NTFS partition and email & firefox were then identical in both.

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

Thank you for your interesting suggestion. I contemplated putting my /home directory on the external drive but decided it would be impractical as Ubuntu would not be able to start if the external drive is not attached. This appears to be a smarter way to achieve the same functionality.

---

