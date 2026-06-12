---
title: "[SOLVED] Damaged packages.."
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by cardpogi on 2008-11-17
Well i think the source of my problems is i had a bad shutdown while i was making an update, ive been googling it.. havent found a solution... Here goes nothing this is what i get..

cardpogi@ubuntu:~$ sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnome-cards-data gnome-games gnome-games-data gnome-settings-daemon
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/15.7MB of archives.
After this operation, 36.9kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/gnome-cards-data_1%3a2.24.1.1-0ubuntu1_all.deb (--unpack):
 files list file for package `ussp-push' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-cards-data_1%3a2.24.1.1-0ubuntu1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2008-11-17
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by cardpogi on 2008-11-17
cardpogi@ubuntu:~$ sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support
  firefox-gnome-support gnome-cards-data gnome-games gnome-games-data
  gnome-settings-daemon xulrunner-1.9 xulrunner-1.9-gnome-support
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8881kB/24.6MB of archives.
After this operation, 41.0kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.10.1 [39.4kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.10.1 [7534kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.10.1 [84.1kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main firefox-3.0-branding 3.0.4+nobinonly-0ubuntu0.8.10.1 [202kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.10.1 [885kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main firefox 3.0.4+nobinonly-0ubuntu0.8.10.1 [68.7kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.10.1 [68.6kB]
Fetched 8881kB in 4min33s (32.4kB/s)                                           
(Reading database ... dpkg: error processing /var/cache/apt/archives/xulrunner-1.9-gnome-support_1.9.0.4+nobinonly-0ubuntu0.8.10.1_i386.deb (--unpack):
 files list file for package `ussp-push' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/xulrunner-1.9-gnome-support_1.9.0.4+nobinonly-0ubuntu0.8.10.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2008-11-17
Try:
sudo apt-get clean
sudo apt-get dist-upgrade

---

### Post by cardpogi on 2008-11-17
cardpogi@ubuntu:~$ sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gnome-cards-data
  gnome-games gnome-games-data gnome-settings-daemon xulrunner-1.9 xulrunner-1.9-gnome-support
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.6MB of archives.
After this operation, 41.0kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.10.1 [39.4kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.10.1 [7534kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.10.1 [84.1kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main firefox-3.0-branding 3.0.4+nobinonly-0ubuntu0.8.10.1 [202kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.10.1 [885kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main firefox 3.0.4+nobinonly-0ubuntu0.8.10.1 [68.7kB]   
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.10.1 [68.6kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main gnome-cards-data 1:2.24.1.1-0ubuntu1 [428kB]       
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main gnome-games-data 1:2.24.1.1-0ubuntu1 [13.9MB]      
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main gnome-games 1:2.24.1.1-0ubuntu1 [1099kB]          
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main gnome-settings-daemon 2.24.0-0ubuntu3.2 [292kB]   
Fetched 24.6MB in 8min31s (48.1kB/s)                                                                        
(Reading database ... dpkg: error processing /var/cache/apt/archives/xulrunner-1.9-gnome-support_1.9.0.4+nobinonly-0ubuntu0.8.10.1_i386.deb (--unpack):
 files list file for package `ussp-push' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/xulrunner-1.9-gnome-support_1.9.0.4+nobinonly-0ubuntu0.8.10.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by cariboo on 2008-11-17
You have to fix this: **ussp-push** before you can contnue. Go  to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages and fix the broken package first.

Jim

---

### Post by cardpogi on 2008-11-18
Tried it.. :( it finished by saying all dependencies issues have been resolved, then tried pumalite's steps with same result, so i tried reinstalling ussp-push but it wouldn't work.. :/ get the same error message ussp-push missing final line.. :/

---

### Post by Pumalite on 2008-11-18
Try:
sudo dpkg --remove --force-remove-reinstreq ussp-push
Then run the commands.
Then reinstall it if need be

---

### Post by cardpogi on 2008-11-18
cardpogi@ubuntu:~$ sudo dpkg --remove --force-remove-reinstreq ussp-push

(Reading database ... dpkg: error processing ussp-push (--remove):
 files list file for package `ussp-push' is missing final newline
Errors were encountered while processing:
 ussp-push
Processing was halted because there were too many errors.

Reinstall what? U mean the OS?

---

### Post by Pumalite on 2008-11-18
Try:
sudo apt-get remove --purge ussp-push

---

### Post by cardpogi on 2008-11-18
cardpogi@ubuntu:~$ sudo apt-get remove --purge ussp-push

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ussp-push*
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
After this operation, 81.9kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing ussp-push (--purge):
 files list file for package `ussp-push' is missing final newline
Errors were encountered while processing:
 ussp-push
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


:(

---

### Post by cardpogi on 2008-11-18
Im not sure if this helps, but my problem was when i was instaling the ussp-push to transfer some files over bluetooth my computer ran out of power and shutdown... not sure if tihs info helps... im guessing the installation was corrupted and the OS want's some files or code it cant find...

---

### Post by cardpogi on 2008-11-18
Thanks guys for all the help got it fixed.. look at what i did...i went.. /var/lib/dpkg and deleted all the info on ussp-push in the available file and in the status file and then reinstalled it... everything seem to be working fine ill give a post up if anything goes wrong.

---

