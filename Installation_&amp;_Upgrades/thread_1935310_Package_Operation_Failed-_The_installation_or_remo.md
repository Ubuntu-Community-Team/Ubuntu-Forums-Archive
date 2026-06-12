---
title: "Package Operation Failed- The installation or removal of a software package failed."
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by Devon12 on 2012-03-04
Hey guys I'm new to ubuntu. For a while I was able to download packages from the software center, but recently I tried to install wine and got the above error. The weird thing is, I can download packages from the software center but I can't install them. I did google this problem and I saw people had similar problems but they weren't the exact same and being new to this I really didn't know how to learn from it. Anyway the error message I get is as follows:


```
installArchives() failed: 
Extracting templates from packages: 61%
Extracting templates from packages: 100%
Preconfiguring packages ...

Extracting templates from packages: 61%
Extracting templates from packages: 100%
Preconfiguring packages ...

Extracting templates from packages: 61%
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package libunistring0.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `gnome-session-common' contains empty filename
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

```

Any help would be appreciated guys thanks.

---

### Post by Paddy Landau on 2012-03-04
I believe Wine is already installed by default; I may be wrong. Did you try to install Wine the normal way, through the Ubuntu Software Centre?

What, specifically, did you do that gave the error message? Did you find Wine on the Ubuntu Software Centre and then press Install?

Try entering the following commands in the terminal (close the Ubuntu Software Centre first):
```
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
```If those complete successfully, open Ubuntu Software Centre and [install Wine]("apt:wine").

I strongly recommend that you also [install PlayOnLinux]("apt:playonlinux"). Wine is complicated to use; PlayOnLinux is a front-end to Wine that hides its complexity and makes it easy to install, configure and uninstall Windows programs.

Please be aware that Wine is an imperfect solution. Most Windows programs won't work; some will; and others will work but with problems. Refer to [the Wine database]("http://appdb.winehq.org/") to find if your Windows program has been tested and, if so, how well it is likely to run.

---

### Post by Devon12 on 2012-03-04
Thanks for your reply. I got that error message when I tried installing wine from software center, I tried to install other packages from the software center as well, then I also got a similar error when I tried to install updates. Here is the output from the suggested codes:

```
devon@devon-Satellite-A105:~$ sudo apt-get --fix-broken install
[sudo] password for devon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
devon@devon-Satellite-A105:~$ sudo dpkg --configure --pending
devon@devon-Satellite-A105:~$ sudo apt-get update
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted TranslationIndex
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Ign http://extras.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric InRelease                         
Hit http://extras.ubuntu.com oneiric Release.gpg
Ign http://us.archive.ubuntu.com oneiric-updates InRelease
Ign http://us.archive.ubuntu.com oneiric-backports InRelease
Hit http://extras.ubuntu.com oneiric Release   
Ign http://us.archive.ubuntu.com oneiric-security InRelease
Hit http://us.archive.ubuntu.com oneiric Release.gpg
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security Release.gpg
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric Release
Hit http://us.archive.ubuntu.com oneiric-updates Release              
Hit http://us.archive.ubuntu.com oneiric-backports Release            
Hit http://us.archive.ubuntu.com oneiric-security Release             
Hit http://us.archive.ubuntu.com oneiric/main Sources                 
Hit http://us.archive.ubuntu.com oneiric/restricted Sources
Hit http://us.archive.ubuntu.com oneiric/universe Sources
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources
Ign http://extras.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/main Sources
Hit http://us.archive.ubuntu.com oneiric-security/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-security/universe Sources
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-security/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/universe Translation-en
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
devon@devon-Satellite-A105:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg file-roller
  libxml2 python-httplib2 python-libxml2 python-pkg-resources ubuntuone-couch
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/24.1 MB of archives.
After this operation, 848 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `gnome-session-common' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Thanks for the suggestion, I will definitely install Playonlinux as soon I can get this problem solved.

---

### Post by cortman on 2012-03-04
Looks like you should comment out (#) the cdrom lines on /etc/apt/sources.list. Run

```
gksu gedit /etc/apt/sources.list
```

Find the lines that have "cdrom" in them, and put a hash mark (#) at the start of the line. Save, and run

```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update

```

And post the results.

---

### Post by Paddy Landau on 2012-03-05
> **cortman said:**
> Looks like you should comment out (#) the cdrom lines on /etc/apt/sources.list. Run...
Correct me if I'm wrong, but you can also do this from the GUI, can't you? In the attachment (*Software Sources*), refer to the bottom section, "Installable from CD-ROM/DVD", and uncheck the box if it is checked.
[attach]213727[/attach]

---

### Post by Devon12 on 2012-03-12
Well I had to reinstall Ubuntu because another problem popped up (just my luck lol) of course it works now. Thanks so much guys, I'm going to go ahead and mark this one as solved

---

### Post by Paddy Landau on 2012-03-12
Sorry you had to solve it by reinstalling!

Here is how to [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

