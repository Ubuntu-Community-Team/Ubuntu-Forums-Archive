---
title: "Local and obsolete packages after upgrading from 16.04 to 16.10"
date: 2016-12-20
forum: Installation &amp; Upgrades
---

### Post by IngerAlHaosului on 2016-12-20
I upgraded from lubuntu 16.04 to 16.10 last month. A few days ago i opened up synaptic to search for a package to install and i found a large number of packages in the Local and obsolete section (where there used to be just 1 i manually installed). I don't use synaptic that often as i prefer to update using apt, so i don't know when they showed up. I know that this packages will not be automatically updated however they appear to be system files and libraries so i am afraid to remove them in case this will break something. Can you please advice me if it is safe to remove them, or if there is a replacement  for them i need to manually update to? The list of packages and their versions are as follows:

initscripts - 2.88dsf-59.3ubuntu2
insserv - 1.14.0-5ubuntu3
libavcodec-ffmpeg56 - 7:2.8.8-0ubuntu0.16.04.1
libavformat-ffmpeg56 - 7:2.8.8-0ubuntu0.16.04.1
libavutil-ffmpeg54 - 7:2.8.8-0ubuntu0.16.04.1
libcamel-1.2-54 - 3.18.5-1ubuntu1
libedataserver-1.2-21 - 3.18.5-1ubuntu1
libguvcview-1.1-1 - 2.0.2+debian-3
libhunspell-1.3-0 - 1.3.3-4ubuntu1
libical1a - 1.0.1-0ubuntu2
libicu55 - 55.1-7
libjson-c2 - 0.11-4ubuntu2
libpackagekit-glib2-16 - 0.8.17-4ubuntu6~gcc5.4ubuntu1.1
libpng12-0 - 1.2.54-1ubuntu1
libpostproc-ffmpeg53 - 7:2.8.8-0ubuntu0.16.04.1
libprocps4 - 2:3.3.10-4ubuntu2.2
libqmi-glib1 - 1.12.6-1
libswresample-ffmpeg1 - 7:2.8.8-0ubuntu0.16.04.1
libswscale-ffmpeg3 - 7:2.8.8-0ubuntu0.16.04.1
libtidy-0.99-0 - 20091223cvs-1.5
libwebp5 - 0.4.4-1
sysv-rc - 2.88dsf-59.3ubuntu2
xserver-xorg-input-vmmouse - 1:13.1.0-1ubuntu2

---

### Post by Impavidus on 2016-12-20
I think they are leftovers from 16.04. I checked libicu55, which is a package installed by default on 16.04. On 16.10, it has been replaced by libicu57.

These packages should have been removed during the last stage of the upgrade to 16.10. Maybe something went wrong. I think you can safely remove them.

---

### Post by IngerAlHaosului on 2016-12-20
A lot of the libraries had newer versions installed and i removed them without problems however some packages do not appear to have a newer equivalent, and this are the scarier ones. 

**initscripts - 2.88dsf-59.3ubuntu2 ** - scripts for initializing and shutting down the system
**insserv - 1.14.0-5ubuntu3** - boot sequence organizer using LSB init.d script dependency information
**sysv-rc - 2.88dsf-59.3ubuntu2** - System-V-like runlevel change mechanism

and to a lesser extent this one
**xserver-xorg-input-vmmouse - 1:13.1.0-1ubuntu2** - X.Org X server -- VMMouse input driver to use with VMWare

---

### Post by ajgreeny on 2016-12-20
You will find that running ```
sudo apt-get -s autoremove
```will show you if they are to be removed by that command.
If so, re-run that command but remove the **-s** option (simulate) and they will all be removed for you.

---

### Post by IngerAlHaosului on 2016-12-20
i have run apt autoremove many times and this packages do not show up as auto removable. I tried the command you provided and there were no packages to auto remove.

root@vlad-Aspire-one:~# apt-get -s autoremove
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by ajgreeny on 2016-12-20
In that case I would probably suggest you leave them where they are, unless you are really running short of disk space.  If they are not being used by the system they will not slow down your computer in the manner extra applications can do in Windows, for example.

You could try removing them one at a time and see if it upsets anything, or if each one takes with it something that you know is needed.

---

