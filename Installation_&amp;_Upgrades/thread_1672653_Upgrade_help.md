---
title: "Upgrade help"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by M1C4HTRON13 on 2011-01-21
i get this when trying to update.
heres what it say's in the details.

installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 1: unexpected EOF while looking for matching `"'
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 install-info
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 1: unexpected EOF while looking for matching `"'
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 install-info

---

### Post by sikander3786 on 2011-01-21
Try these commands and post the complete outputs.

Applications > Accessories > Terminal:

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by M1C4HTRON13 on 2011-01-21
```
micah@M1C4HTR0N:~$ sudo dpkg --configure -a
[sudo] password for micah: 
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 1: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install-info

```

```
micah@M1C4HTR0N:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xplanet xplanet-images
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 1: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by sikander3786 on 2011-01-21
One by one,

```
sudo apt-get remove --purge install-info
```

```
sudo apt-get install install-info
```

---

### Post by M1C4HTRON13 on 2011-01-21
```
micah@M1C4HTR0N:~$ sudo apt-get remove --purge install-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdebase-workspace libkscreensaver5 xplanet plasma-widgets-workspace klipper
  ksysguard libprocesscore4a kwrite libprocessui4a xplanet-images
  kdebase-workspace-bin libplasmagenericshell4 systemsettings kinfocenter
  kdebase-workspace-data plasma-desktop libksignalplotter4
  plasma-widget-folderview kdepasswd
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  info* install-info* kde-plasma-desktop* kdebase-apps* konqueror*
  ubuntu-standard*
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  install-info (due to grep)
0 upgraded, 0 newly installed, 6 to remove and 17 not upgraded.
1 not fully installed or removed.
After this operation, 4,362kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] Yes, do as I say!
(Reading database ... 343777 files and directories currently installed.)
Removing kde-plasma-desktop ...
Removing kdebase-apps ...
Removing konqueror ...
update-alternatives: using /usr/bin/opera to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
Purging configuration files for konqueror ...
Removing ubuntu-standard ...
Removing info ...
Purging configuration files for info ...
Removing install-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IE.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...

```

```
micah@M1C4HTR0N:~$ sudo apt-get install install-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdebase-workspace libkscreensaver5 xplanet plasma-widgets-workspace
  konqueror-nsplugins klipper ksysguard libprocesscore4a dolphin kwrite
  libprocessui4a xplanet-images kdebase-workspace-bin libkonqsidebarplugin4a
  libplasmagenericshell4 kfind systemsettings kinfocenter
  kdebase-workspace-data plasma-desktop libksignalplotter4
  plasma-widget-folderview kdepasswd
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  install-info
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
Need to get 145kB of archives.
After this operation, 258kB of additional disk space will be used.
Get:1 http://ie.archive.ubuntu.com/ubuntu/ maverick/main install-info i386 4.13a.dfsg.1-5ubuntu1 [145kB]
Fetched 145kB in 0s (150kB/s)       
Selecting previously deselected package install-info.
(Reading database ... 343604 files and directories currently installed.)
Unpacking install-info (from .../install-info_4.13a.dfsg.1-5ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 1: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by M1C4HTRON13 on 2011-01-21
I think it's some thing to do with /etc/environment

---

### Post by sikander3786 on 2011-01-21
> **M1C4HTRON13 said:**
> I think it's some thing to do with /etc/environment
In fact it is. I thought a re-install might solve the issue but it didn't. Make sure all of the intended directories exist.

```
ls /usr/local/sbin
ls /usr/local/bin
ls /usr/sbin
ls /usr/bin
ls /sbin
ls /bin
ls /usr/games
```

---

### Post by M1C4HTRON13 on 2011-01-21
this is what it say's

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by M1C4HTRON13 on 2011-01-21
I changed it to
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
and that fixed it
Thanks for your help!!

---

