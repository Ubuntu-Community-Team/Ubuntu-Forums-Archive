---
title: "Unable to update &quot;Ubuntu-whatever version&quot;"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by akoben on 2011-01-18
I am unable to do updates when I try from the update manager
all i get is "waiting for apt-get to exit" but there is not 
another instance of the update manager or the software center 
running. If I do "sudo apt-get update" It starts to update 
but things really start to get strange. (I installed from
a flash drive, it was version 10.10 anyway) I am not asked to 
use the flash drive but to please insert the disc labeled 
Ubuntu 11.04 _Natty Narwhal_ - Alpha i386 (20101214) 
Don't have it, so I downloaded the cd image and when 
I Ioad the cd I get

A volume with software packages has been detected.
Would you like to open it with the package manager?

so I start the package manager and get

E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?

I downloaded this Image from Ubuntu all software image page.
and why is it detecting packages that are not there?

I have not got a clue whats going on, and I need to update the system.

---

### Post by snowpine on 2011-01-19
Welcome to the forums!

Try going to the System, Administration menu and choosing Software Sources. You should see a check-box for the Ubuntu CD-ROM. If you UNcheck this box, Ubuntu should then go to the internet for updates.

If you're still having problems after that, could you please open Applications->Accessories->Terminal and copy & paste the results of the following commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by snowpine on 2011-01-19
Welcome to the forums!

Try going to the System, Administration menu and choosing Software Sources. You should see a check-box for the Ubuntu CD-ROM. If you UNcheck this box, Ubuntu should then go to the internet for updates.

If you're still having problems after that, could you please open Applications->Accessories->Terminal and copy & paste the results of the following commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by adrinkrahene on 2011-01-20
"Try going to the System, Administration menu and choosing Software Sources."

This is interesting... I dont see Software Sources in my menu at all!
Could there be another place? I have check all the places, I think it could be in.
Also I have try the other idea before and it asked for the CD.
  

Thanks!

---

### Post by adrinkrahene on 2011-01-20
additional information...

genetic@Twilight:~/Downloads$ sudo apt-get upgrade
[sudo] password for genetic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  g++
The following packages will be upgraded:
  apparmor apparmor-utils apport apport-gtk aptdaemon brasero brasero-cdrkit brasero-common bsdutils build-essential clamav
  clamav-base clamav-docs clamav-freshclam clamav-testfiles cups cups-bsd cups-client cups-common cups-ppdc dbus dbus-x11
  dkms dpkg dpkg-dev evince evince-common evolution evolution-common evolution-plugins fuse-utils gnome-system-tools
  ifupdown libalgorithm-diff-perl libalgorithm-merge-perl libapparmor-perl libapparmor1 libblkid1 libbrasero-media1
  libc-bin libc-dev-bin libc6 libc6-dev libclamav6 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1
  libcupsppdc1 libdbus-1-3 libdpkg-perl libevdocument3 libevolution libevview3 libfuse2 liblcms1 libpam-smbpass
  libparted0debian1 libsmbclient libsqlite3-0 libuuid1 libvlc5 libvlccore4 libwbclient0 libx264-98 mount parted patch
  python-apport python-aptdaemon python-aptdaemon-gtk python-problem-report samba samba-common samba-common-bin samba-doc
  smbclient swat ubuntu-sso-client util-linux uuid-runtime vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse
  xserver-common xserver-xorg-core
89 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 37.0MB/89.8MB of archives.
After this operation, 164kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main mount i386 2.17.2-0ubuntu1.10.10.1 [174kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main util-linux i386 2.17.2-0ubuntu1.10.10.1 [527kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main bsdutils i386 1:2.17.2-0ubuntu1.10.10.1 [80.2kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main libuuid1 i386 2.17.2-0ubuntu1.10.10.1 [61.6kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main libblkid1 i386 2.17.2-0ubuntu1.10.10.1 [110kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main libparted0debian1 i386 2.3-2ubuntu2 [229kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main parted i386 2.3-2ubuntu2 [74.1kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main brasero-common all 2.32.0-0ubuntu2.1 [357kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main brasero-cdrkit i386 2.32.0-0ubuntu2.1 [35.4kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main libdbus-1-3 i386 1.4.0-0ubuntu1.1 [130kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main brasero i386 2.32.0-0ubuntu2.1 [179kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main libbrasero-media1 i386 2.32.0-0ubuntu2.1 [431kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe swat i386 2:3.5.4~dfsg-1ubuntu8.2 [2,249kB]
Media change: please insert the disc labeled
 'Ubuntu 11.04 _Natty Narwhal_ - Alpha i386 (20101214)'
in the drive '/cdrom/' and press enter

Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main samba i386 2:3.5.4~dfsg-1ubuntu8.2 [7,450kB]              
Media change: please insert the disc labeled                                                                                
 'Ubuntu 11.04 _Natty Narwhal_ - Alpha i386 (20101214)'
in the drive '/cdrom/' and press enter

---

### Post by snowpine on 2011-01-20
> **adrinkrahene said:**
> "Try going to the System, Administration menu and choosing Software Sources."

This is interesting... I dont see Software Sources in my menu at all!
Could there be another place? I have check all the places, I think it could be in.
Also I have try the other idea before and it asked for the CD.
  

Thanks!

Sorry, I am not a Gnome user. Try:

```
gksu gedit /etc/apt/sources.list
```

Find and delete the line referencing the 11.04 CD-ROM, save the file, and try again. :)

---

### Post by adrinkrahene on 2011-01-21
OK that worked like a charm.  The system is now up to date.
by the way I found a few CD versions in there I didn't have
after removing them also the system updated.
                                            Thanks Again!  ;)

---

