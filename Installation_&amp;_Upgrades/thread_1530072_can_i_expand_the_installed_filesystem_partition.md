---
title: "can i expand the installed filesystem partition?"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by house7 on 2010-07-13
Hello. 
Couple weeks ago i installed ubuntu 10.04 with wubi on Windows 7. It works perfectly. And, i've only installed 5GB rather that 20GB in my partition (from the wubi option at the first time). I made this partition only for ubuntu but silly me i've installed only 5GB rather than to chose 20GB :( 

Now the ubuntu is low on disk space! it' only 120MB left from 5GB. My question is, is there any way expand it to 20GB so the partition is fully for home folder, etc? I want my 15GB!

Thank you.

---

### Post by cHayanKs on 2010-07-13
I have same problem with you... I need more space for my Karmic Koala..
Hope Some hear our problem and help to fix it..:confused:

---

### Post by pmlxuser on 2010-07-13
in windows i would use partition magic to expand a partition. however if you installed in windows then a challenge come in. 
The best would be save you settings and data (usually achieved by backing up in another medium) and do a clean installation with the specified setting.
usually a good idea is to have separate partition for os (ie /) root parttion and /home (to store in your data)

---

### Post by garvinrick4 on 2010-07-13
It is a folder inside of Windows in C; drive right next to Users named Ubuntu and I have never found a way to increase the size of a Wubi install.
 It is like an hour of time to uninstall and reinstall in ubuntu folder in Windows. First back up any Home you want to keep. in firefox go Bookmarks to Organize bookmarks to import and backup and choose backup will make a file with .json and you can import it back into firefox after new install. First install medibuntu repository and key, google it easy to install. If starts with deb go to software sources to other software to add and copy and paste in window that opens. While in software sources check partners and make sure all of opening page are checked. Then run this in terminal and while it is upgrading do your panels and menus.
Then do the preferences such as keyboard shortcuts and screensaver and such. Should take no more than an hour to get a nice clean new install with Bells and Whistles installed.
```
 
sudo apt-get install ubuntu-restricted-extras gparted sysinfo libdvdcss2 && sudo apt-get update && sudo apt-get upgrade
```P.S.  ubuntu-restricted-extras gives you flash, java, tty fonts, codecs to run most all music or video players.

---

### Post by house7 on 2010-07-13
> **garvinrick4 said:**
> It is a folder inside of Windows in C; drive right next to Users named Ubuntu and I have never found a way to increase the size of a Wubi install.
 It is like an hour of time to uninstall in ubuntu folder in Windows. First back up any Home you want to keep. in firefox go Bookmarks to Organize bookmarks to import and backup and choose backup will make a file with .json and you can import it back into firefox after new install. First install medibuntu repository and key, google it easy to install. If starts with deb go to software sources to other software to add and copy and paste in window that opens. While in software sources check partners and make sure all of opening page are checked. Then run this in terminal and while it is upgrading do your panels and menus.
Then do the preferences such as keyboard shortcuts and screensaver and such. Should take no more than an hour to get a nice clean new install with Bells and Whistles installed.
```
 
sudo apt-get install ubuntu-restricted-extras gparted sysinfo libdvdcss2 && sudo apt-get update && sudo apt-get upgrade
```P.S.  ubuntu-restricted-extras gives you flash, java, tty fonts, codecs to run most all music or video players.

Geez.. I never think about uninstall. I think that is the best method.
But i found [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?) 

Can i do with that method?
Well, gotta do the wubi guide first now, and then if that doesn't work, do clean install.

---

### Post by house7 on 2010-07-14
okay, uninstall and then clean install with wubi, works like charm. it only took like less than 5 minutes to uninstall!!

---

### Post by garvinrick4 on 2010-07-14
> **house7 said:**
> okay, uninstall and then clean install with wubi, works like charm. it only took like less than 5 minutes to uninstall!! Good, It is also
good practice to set up your gnome desktop and get the right packages installed. Once you
get used to Ubuntu there is always something new happening and every 6 months a new version.8.04,8.10 9.04, 9.10, 10,04,10.10 and on and on she will go.

---

