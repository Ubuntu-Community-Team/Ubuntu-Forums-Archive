---
title: "unable to upgrade dapper after install"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by JavaNet Geek on 2011-07-20
:confused: ok People, here is my probelm. 
we got an old dell PE2450 which just had a hd failure. we`ve reinstalled dapper as this is the only way to install the base system. (we know it`s EOL) but then we upgrade the release. the repositories have been move to old-releases.ubuntu.com. we adjusted the sources list as need. but we are unable to do a release upgrade. we have tried do cdrom upgrades and adding repository to the sources list. but to no avail.

any ideas / suggestions would be gratfully received :P

---

### Post by ajgreeny on 2011-07-20
You can't upgrade that version, I'm afraid, as the next LTS version 8.04 is also EOL.  Even if you could do so, it really would be a long winded and pointless job as you would need to go from 6.06 to 8.04 and then 8.04 to 10.04, so you would be downloading twice as much as necessary.

It will be much more sensble to simply download the latest version, either 10.04 LTS, or if you are adventurous and want to see unity, get 11.04.  I would choose 10.04 personally, but that's just my choice.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by JavaNet Geek on 2011-07-20
Hi algreeny
                      we would do as you suggest, but for some reasons the dell pe2450 serverwill only install starting at 6.04lts. all of the later release just frezze during install. so back to sqaure one. thanks anyway :D

---

### Post by JavaNet Geek on 2011-07-20
update for those out there just looked at the log file for the dist-upgrade. every time we enter `sudo do-release-upgrade` it seems it`s trying to access a repo that isn`t there any more but else where        2011-07-20 18:28:36,808 INFO release-upgrader version '0.87.31' started 2011-07-20 18:28:36,825 DEBUG Using 'DistUpgradeViewText' view 2011-07-20 18:28:37,161 DEBUG enable dpkg --force-overwrite 2011-07-20 18:28:37,480 DEBUG lsb-release: 'dapper' 2011-07-20 18:28:37,481 DEBUG _pythonSymlinkCheck run 2011-07-20 18:28:39,548 DEBUG checkViewDepends() 2011-07-20 18:28:39,550 DEBUG need backports 2011-07-20 18:28:39,550 DEBUG getRequiredBackports() 2011-07-20 18:28:39,552 DEBUG writing prereuists sources.list at: '/etc/apt/sources.list.d/prerequists-sources.dapper.list'  2011-07-20 18:28:39,915 DEBUG adding '# sources.list fragment for pre-requists (mirror from sources.list + fallback) ' prerequists 2011-07-20 18:28:39,916 DEBUG adding '# this is safe to remove after the upgrade ' prerequists 2011-07-20 18:28:39,917 DEBUG adding ' ' prerequists 2011-07-20 18:28:39,917 DEBUG adding 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main/debian-installer ' prerequists 2011-07-20 18:28:39,918 DEBUG running doUpdate() (showErrors=False) 2011-07-20 18:28:46,539 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80] '. Retrying (currentRetry: 0) 2011-07-20 18:28:49,036 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80] '. Retrying (currentRetry: 1) 2011-07-20 18:28:51,545 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.171 80] '. Retrying (currentRetry: 2) 2011-07-20 18:28:51,546 ERROR doUpdate() failed completely 2011-07-20 18:28:57,765 ERROR Can not find backport 'release-upgrader-apt' 2011-07-20 18:28:57,766 DEBUG writing prereuists sources.list at: '/etc/apt/sources.list.d/prerequists-sources.dapper.list'  2011-07-20 18:28:58,115 DEBUG adding '# sources.list fragment for pre-requists (mirror from sources.list + fallback) ' prerequists 2011-07-20 18:28:58,115 DEBUG adding '# this is safe to remove after the upgrade ' prerequists 2011-07-20 18:28:58,116 DEBUG adding 'deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main/debian-installer deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main/debian-installer deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main/debian-installer deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) dapper-backports main/debian-installer  ' prerequists 2011-07-20 18:28:58,116 DEBUG adding 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main/debian-installer ' prerequists 2011-07-20 18:28:58,117 DEBUG running doUpdate() (showErrors=False) 2011-07-20 18:29:00,783 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80] '. Retrying (currentRetry: 0) 2011-07-20 18:29:03,362 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80] '. Retrying (currentRetry: 1) 2011-07-20 18:29:06,013 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80] '. Retrying (currentRetry: 2) 2011-07-20 18:29:06,014 ERROR doUpdate() failed completely        anyone know which script to change? if there is a way. Thanks

---

### Post by JavaNet Geek on 2011-07-20
Ok did find this but doen`t tell what i all ready know, it might need updating
 
[https://help.ubuntu.com/community/EOLUpgrades#6.06](https://help.ubuntu.com/community/EOLUpgrades#6.06) to 8.04.3 (Dapper to Hardy)

---

### Post by mörgæs on 2011-07-20
It would be better to find out why the new releases are freezing. Please post the hardware specifications.

Are you installing the desktop or server version?

If the first, have you tried the alternate ISO?

---

### Post by JavaNet Geek on 2011-07-20
thank for replying mörgæs
 
the probelm is more to do with upgrding, the Dell PowerEdge 2450 server won`t do any clean install above 6.04, could kernal / driver issues. it just freezes if you google it you will see.
so we reinstalled 6.04 server lts. changed sources list to uses the old-releases depository.
no probelm with updates.
But it won`t upgrade to 8.04lts  using do-release-upgrade. which it should but it won`t do it. :confused: so totally stuck as to why.
 
it does keep saying that is unable to get the prerequisites for the upgrade
dist-upgrade log is attached

---

### Post by JavaNet Geek on 2011-07-30
Okay we solved the probelm after a bit of googling and trying a few of them out.
for those that hit the same probelm.
 
[SIZE=3][FONT=Calibri]The best procedure to upgrade Dappy 6.06LTS is as follows[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Make sure the server is up to date, if not[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Change the soures list[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]`[/SIZE][/FONT][FONT=Courier New]Sudo  vi /etc/apt/sources.list[/FONT][SIZE=3][FONT=Calibri]`[/FONT][/SIZE]
[FONT=Courier New][SIZE=3]#Required[/SIZE][/FONT]
[FONT=Courier New]deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper main restricted universe multiverse[/FONT]
[FONT=Courier New]deb http:// old-releases.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse[/FONT]
[FONT=Courier New]deb http:// old-releases.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]# Optional[/FONT]
[FONT=Courier New]#deb http:// old-releases.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse[/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]Then[/FONT][/SIZE][/FONT]
[FONT=Courier New]`sudo apt-get install update-manager-core[/FONT]
[FONT=Courier New]`sudo apt-get update`[/FONT]
[FONT=Courier New]`sudo apt-get install ssh`[/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri](you may need this if the desktop GUI logon doesn`t work after the cdrom upgrade.)[/FONT][/SIZE][/FONT]
[FONT=Courier New]`sudo apt-get install ubuntu-desktop`[/FONT]
[FONT=Courier New](gets rid of any dependency issues plus makes it easy to mount the iso image later.)[/FONT]
[FONT=Courier New]`sudo apt-get upgrade`[/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]Logon via the desktop GUI[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]Then download[/FONT][/SIZE][/FONT]
[FONT=Calibri][[FONT=Times New Roman][FONT=Calibri][SIZE=3][COLOR=#0000ff]http://releases.ubuntu.com/8.04/ubuntu-8.04.4-alternate-i386.iso[/COLOR][/SIZE][/FONT][/FONT]]("http://releases.ubuntu.com/8.04/ubuntu-8.04.4-alternate-i386.iso")[/FONT][FONT=Times New Roman][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]to the desktop[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]mount the image[/FONT][/SIZE][/FONT]
[FONT=Courier New]`[/FONT][COLOR=black][FONT=Courier New]sudo mount -o loop ~/Desktop/ubuntu-8.04-alternate-i386.iso /media/cdrom0`[/FONT][/COLOR][FONT=Courier New][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]then proceed to do a cdrom upgrade [/FONT][/SIZE][/FONT]
[FONT=Courier New]`[/FONT][COLOR=black][FONT=Courier New]sudo /media/cdrom/cdromupgrade`[/FONT][/COLOR][FONT=Courier New][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]after the upgrade you may find you are unable to logon via the desktop GUI[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]if so you should be able to logon via SSH using putty.[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]You now need to change /etc/apt/sources.list[/FONT][/SIZE][/FONT]
[FONT=Courier New]`sudo vi /etc/apt/sources.list`[/FONT]
[FONT=Courier New]# Required[/FONT]
[FONT=Courier New]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse[/FONT]
[FONT=Courier New]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse[/FONT]
[FONT=Courier New]deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]# Optional[/FONT]
[FONT=Courier New]#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse[/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]Exit vi editor[/FONT][/SIZE][/FONT]
[FONT=Courier New]`sudo apt-get update`[/FONT]
[FONT=Courier New]`sudo apt-get upgrade`[/FONT]
[FONT=Courier New]`sudo tasksel` [/FONT]
[FONT=Courier New](remove ubuntu-desktop from the installation.)[/FONT]
[FONT=Courier New]You server is now 8.04LTS to check `[/FONT][FONT=Calibri]lsb_release –a`[/FONT]
[FONT=Calibri]:guitar:\\:D/[/FONT]

---

