---
title: "[SOLVED] Installation problem with gnomes-games-data"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by gcman2 on 2008-07-27
Hi,
 
During one of the last updates, something went wrong with gnomes-games-data. I have tried what I know to try to remove and re-install through both Synaptic and with apt-get, but am in a catch 22: When trying to remove gnomes-games-data, I get this error:

sudo apt-get autoremove gnome-games-data

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-games-data
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 38.1MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing gnome-games-data (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gnome-games-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

But I also get an error when I try the re-install:

sudo apt-get install --reinstall gnome-games-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  gnome-games gnome-games-extra-data
The following packages will be upgraded:
  gnome-games-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/11.5MB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package gnome-games-data.
(Reading database ... 141169 files and directories currently installed.)
Preparing to replace gnome-games-data 1:2.22.3-0ubuntu1 (using .../gnome-games-data_1%3a2.22.3-0ubuntu2_all.deb) ...
Warning: /usr/share/gconf/schemas/aisleriot.schemas could not be found.
Warning: /usr/share/gconf/schemas/blackjack.schemas could not be found.
Warning: /usr/share/gconf/schemas/glchess.schemas could not be found.
Warning: /usr/share/gconf/schemas/glines.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnect.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnibbles.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnobots2.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnometris.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnomine.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotravex.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotski.schemas could not be found.
Warning: /usr/share/gconf/schemas/gtali.schemas could not be found.
Warning: /usr/share/gconf/schemas/iagno.schemas could not be found.
Warning: /usr/share/gconf/schemas/mahjongg.schemas could not be found.
Warning: /usr/share/gconf/schemas/same-gnome.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
WARNING: /usr/share/python-support/gnome-games-data does not exist.
         Some bytecompiled files may be left behind.
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 269, in <module>
    args.remove(arg)
ValueError: list.remove(x): x not in list
dpkg: error processing /var/cache/apt/archives/gnome-games-data_1%3a2.22.3-0ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/gnome-games-data does not exist
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games-data_1%3a2.22.3-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm pretty new to Linux and ubuntu, so any help would be greatly appreciated :)

---

### Post by Pumalite on 2008-07-27
Look for the package in /var/lib/dpkg/status and make it install...ok...installed
Then:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by gcman2 on 2008-07-27
Pumalite,
Well I tried as you suggested, and got the following: 

sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package gnome-games-data needs to be reinstalled, but I can't find an archive for it.


I thought that was odd so I went to look for it....

cd /var/cache/apt/archives

ls gnome*
[only relevant results here......gcman2]
gnome-games_1%3a2.22.3-0ubuntu2_i386.deb
gnome-games-data_1%3a2.22.1.1-0ubuntu3_all.deb
gnome-games-data_1%3a2.22.3-0ubuntu2_all.deb
gnome-cards-data_1%3a2.22.2.1-0ubuntu1_all.deb  
gnome-cards-data_1%3a2.22.2.1-0ubuntu2_all.deb  
gnome-cards-data_1%3a2.22.3-0ubuntu1_all.deb    
gnome-cards-data_1%3a2.22.3-0ubuntu2_all.deb 

So it looks to me like the 2.22.3-0ubuntu2 versions of both gnome-games and gnome-game-data (and gnome-cards-data) are there in the archives....

When I went back to the 'status' file that I edited, this seems to be the version it thinks it wants...

I'm puzzled ... any suggestions what I should try next?
And thanks so much for helping me out....

gcman2

---

### Post by gcman2 on 2008-07-27
More info ... when rebooting the computer, I now get a red warning icon in the top right panel; it tells me the bit about needing to re-install the package gnome-games-data but that it can't find the archive. It says the problem is usually due to unmet dependencies, and it suggests I run Synaptic..... but when I do Synaptic gives me this error as soon as it starts:

E: The package gnome-games-data needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

...and then immediately closes. Who should I report this to?

Still lost, but at least I'm learning stuff that should help me in the future....

---

### Post by Pumalite on 2008-07-27
Have you tried reinstalling the package?
You might have to leave the status file as it was

---

### Post by gcman2 on 2008-07-27
OK, I went back to 'status' to change it back, and discovered I made a mistake the first time... I had inadvertently changed 'gnome-games' from 'install ok unpacked' instead of 'gnome-games-data' :(

So I changed 'gnome-games' back to what it was, and changed 'gnome-games-data' from 'install reinstreq half-configured' to 'install ok installed'

now when I do the upgrade.....

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 19696 package `gnome-games-data':
 Configured-Version for package with inappropriate Status
E: Sub-process /usr/bin/dpkg returned an error code (2)

So at least I get a different error :( :confused:

Can you tell me a little bit about what the 'status' file is doing?

As before, thanks....

---

### Post by gcman2 on 2008-07-27
Again, more info ... the section from the old 'status' file is as follows:

Package: gnome-games-data
Status: install reinstreq half-configured
Priority: optional
Section: gnome
Installed-Size: 37176
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: all
Source: gnome-games
Version: 1:2.22.3-0ubuntu1
Config-Version: 1:2.22.2.1-0ubuntu2
Replaces: glchess, gnome-card-games, gnome-cards-data (<< 1:2.20.3-1), gnome-games-locale, gnome-sudoku
Depends: gconf2 (>= 2.10.1-2), gnome-cards-data (>= 1:2.22), gnome-cards-data (<< 1:2.23), python (>= 2.5), python-support (>= 0.7.1)
Recommends: gnome-games, gnome-games-extra-data
Conflicts: glchess (<< 2.22), gnome-games (<= 1:2.10.1-2), gnome-icon-theme (<< 2.14), gnome-sudoku (<< 2.22)
Description: data files for the GNOME games
 This package contains the data files, sound and pictures used by the
 GNOME games.
Homepage: [http://www.gnome.org/projects/gnome-games/](http://www.gnome.org/projects/gnome-games/)
Original-Maintainer: Josselin Mouette <joss@debian.org>

In the new version I changed it to read install ok installed in the Status: line as suggested.....

---

### Post by gcman2 on 2008-07-28
Hi Pumalite and others,

Well after a night's sleep I think I found the answer.

I looked around in this forum, doing a search for 'get rid of package' ... I found a similar thread marked [solved] that followed a similar tact using the 'status' file. Solution follows:

1. I changed the Status: line for my bad package to 'deinstall ok config-files'
2. sudo apt-get update
   [normal response]

3. sudo apt-get dist-upgrade
   [following response]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-games: Depends: gnome-games-data (>= 1:2.22) but it is not installed
               Depends: gnome-games-data (< 1:2.23) but it is not installed
E: Unmet dependencies. Try using -f.

4. After checking out 'man apt-get' to see what the -f option does;
sudo apt-get -f install
[following response]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gnome-games-data
Recommended packages:
  gnome-games-extra-data
The following NEW packages will be installed:
  gnome-games-data
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 11.5MB of archives.
After this operation, 38.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gnome-games-data 1:2.22.2.1-0ubuntu1 [11.5MB]
Fetched 11.5MB in 60s (189kB/s)                                                                    
Selecting previously deselected package gnome-games-data.
(Reading database ... 141229 files and directories currently installed.)
Unpacking gnome-games-data (from .../gnome-games-data_1%3a2.22.2.1-0ubuntu1_all.deb) ...
Setting up gnome-games-data (1:2.22.2.1-0ubuntu1) ...

Setting up gnome-games (1:2.22.3-0ubuntu2) ...

And now, all seems FIXED :)

Thanks Pumalite, you rock.... hope this post helps others, and that I can figure out how to mark it as [solved].

---

### Post by Pumalite on 2008-07-28
You are welcome. Congrats!

---

