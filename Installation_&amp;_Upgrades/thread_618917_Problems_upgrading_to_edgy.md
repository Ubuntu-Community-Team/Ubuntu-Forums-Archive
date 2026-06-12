---
title: "Problems upgrading to edgy"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by n.jin on 2007-11-20
hi iam new to ubuntu/linux and having problem with uypgrading my copy 6.06 to 6.10
iam planning to use 7.10 but i cant skip upgrades so iam upgrading to versionone by one now the problem is when i click on the check button onupdate manager it gives me this result


> W: GPG error: [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


and when i do

```
gksu "update-manager -c"
```

i get this message at the terminal
> 
(update-manager:7753): Gdk-WARNING **: locale not supported by Xlib

(update-manager:7753): Gdk-WARNING **: cannot set locale modifiers
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)


ut i get to see the upgrade to 6.10 but at the part where is says Modifying software channels i get this error message

> 
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.bz2) MD5Sum mismatch

what should i do next?

---

### Post by Martin T Wirth on 2007-11-21
MD5 checksum mismatch indicates that the file was corrupted during the download. Try downloading again. If this is a frequent problem, your modem or network card my be needing replacement.

Your upgrade path is a very difficult way to get to 7.10 Gutsy Gibbon. I have had difficulty getting perfect upgrades because some files such as hardware drivers may be left over from the old version on each upgrade. I recommend backing up all the data that you want to keep and doing a clean installation. I also recommend a such a backup prior to upgrading anyway.

If you clean or separate large unnecessary files out of your home directory, then you can **cp -r **backup your entire home/user directory to a USB harddisk or memory card. This is likely to preserve your environment, desktop preferences, browser bookmarks, and emails for a full restoration after you've done a clean installation.

Best of luck.

---

### Post by zvacet on 2007-11-21
In Dapper run this

```
sudo aptitude update && sudo aptitude upgrade
```

After that you should be able to upgrade to Edgy.

---

### Post by n.jin on 2007-11-21
> MD5 checksum mismatch indicates that the file was corrupted during the download. Try downloading again. If this is a frequent problem, your modem or network card my be needing replacement.

Your upgrade path is a very difficult way to get to 7.10 Gutsy Gibbon. I have had difficulty getting perfect upgrades because some files such as hardware drivers may be left over from the old version on each upgrade. I recommend backing up all the data that you want to keep and doing a clean installation. I also recommend a such a backup prior to upgrading anyway.

If you clean or separate large unnecessary files out of your home directory, then you can cp -r backup your entire home/user directory to a USB harddisk or memory card. This is likely to preserve your environment, desktop preferences, browser bookmarks, and emails for a full restoration after you've done a clean installation.

Best of luck.

reason to all this is that i already have a cd installer for dapper but i want i want to use the most recent version and iam trying to avoid downloading a copy since i dont have a cd burner right now, a memory stick thats already full (contains all my backup files)
but i will try your suggestion as a last resort thanks for the reply


> 
In Dapper run this

Code:

sudo aptitude update && sudo aptitude upgrade

After that you should be able to upgrade to Edgy.

try this now, hope this one would do it

---

### Post by n.jin on 2007-11-21
ok the code 

```
sudo aptitude update && sudo aptitude upgrade 
```

worked just fine , now iam at 6.10 , thanks!

but now  iam upgrading from 6.10 to 7.04 then lastly 7.10, but along the upgrade from 6.10 to 7.04 i get this message from update manager

 > Error authenticating some packages

and gives me this list

> app-install-data
app-install-data-commercial
apport
apport-gtk
bind9-host
bsdutils
capplets-data
cdrecord
cupsys
cupsys-bsd
cupsys-client
cupsys-common
dbus
dbus-1-utils
dnsutils
evolution-data-server
evolution-data-server-common
file
firefox
firefox-gnome-support
genisoimage
gimp
gimp-data
gimp-python
gnome-app-install
gnome-control-center
gnome-panel
gnome-panel-data
hpijs
hplip
hplip-data
hwdb-client-common
hwdb-client-gnome
iptables
language-pack-en
libbind9-0
libcamel1.2-10
libcupsimage2
libcupsys2
libcurl3
libcurl3-gnutls
libdbus-1-3
libdns22
libebook1.2-9
libecal1.2-7
libedata-book1.2-2
libedata-cal1.2-6
libedataserver1.2-9
libedataserverui1.2-8
libegroupwise1.2-13
libexchange-storage1.2-3
libexif12
libfreetype6
libgd2-xpm
libgimp2.0
libgl1-mesa-dri
libgl1-mesa-glx
libglu1-mesa
libgnome-window-settings1
libisc11
libisccc0
libisccfg1
libjasper-1.701-1
libkrb53
liblwres9
libmagic1
libmagick9
libmetacity0
libmysqlclient15off
libnspr4
libnss3
libpanel-applet2-0
libpng12-0
libpoppler1
libpoppler1-glib
libpq5
libslab0
libsmbclient
libsndfile1
libssl0.9.8
libvorbis0a
libvorbisenc2
libvorbisfile3
libwrap0
linux-386
linux-headers-2.6.20-16
linux-headers-2.6.20-16-generic
linux-headers-generic
linux-image-2.6.20-16-386
linux-image-386
linux-restricted-modules-2.6.20-16-386
linux-restricted-modules-386
linux-restricted-modules-common
mesa-utils
metacity
metacity-common
mkisofs
mount
mysql-common
openoffice.org
openoffice.org-base
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-evolution
openoffice.org-filter-mobiledev
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-java-common
openoffice.org-l10n-en-us
openoffice.org-math
openoffice.org-style-andromeda
openoffice.org-style-default
openoffice.org-style-human
openoffice.org-style-industrial
openoffice.org-writer
openssl
poppler-utils
python
python-apport
python-examples
python-gdbm
python-launchpad-bugs
python-minimal
python-problem-report
python-tk
python-uno
python2.5
python2.5-examples
python2.5-minimal
rdesktop
rsync
samba-common
smbclient
tar
tcpd
tcpdump
tk8.4
ttf-opensymbol
tzdata
unattended-upgrades
update-manager
update-manager-core
util-linux
util-linux-locales
vim
vim-common
vim-runtime
vim-tiny
wodim
xscreensaver-data
xscreensaver-gl

 now i did a little searching over the forums and found similar threads and did a couple of steps but it didnt work iam still getting the same error

now iam thinking should i just uninstall those packages that its having problems with, since initialy the reason i had those installed is that i have read that i need the current version up-to-date before trying to upgrade to a new dist. Is it advisable to do that?

thanks

---

### Post by zvacet on 2007-11-21
Did you replaced everything fromDapper to Edgy in your source list?If you didn´t type this in terminal

```
sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list
```

After that you need your Edgy to be up-to-date.

```
sudo aptitude update && sudo aptitude upgrade
```

After that you can do the upgrade to Feisty.

[https://help.ubuntu.com/community/FeistyUpgrades?highlight=%28upgrades%29%7C%28feisty%29]("https://help.ubuntu.com/community/FeistyUpgrades?highlight=%28upgrades%29%7C%28feisty%29")

---

### Post by n.jin on 2007-11-22
> **zvacet said:**
> Did you replaced everything fromDapper to Edgy in your source list?If you didn´t type this in terminal

```
sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list
```

After that you need your Edgy to be up-to-date.

```
sudo aptitude update && sudo aptitude upgrade
```

After that you can do the upgrade to Feisty.

[https://help.ubuntu.com/community/FeistyUpgrades?highlight=%28upgrades%29%7C%28feisty%29]("https://help.ubuntu.com/community/FeistyUpgrades?highlight=%28upgrades%29%7C%28feisty%29")

tried that as you have said, but i still get the same error

---

### Post by zvacet on 2007-11-22
Do you have all repos open?

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by n.jin on 2007-11-22
thanks,

for some reason it went thru this time. so my desktop pc is 7.04, thanks zvacet! for now i think i'll stop at 7.04 at the moment

now iam installing another copy of ubuntu to a friends pc, i did a 
```

sudo aptitude update && sudo aptitude upgrade
``` 

directy after fresh install, work just fine, though at the terminal after reboot i did a sudo update and upgrade again just to make sure part of the result says this

> W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

i dont know if that has something to do with my next problem

as i do the gksu "update-manager -c"

again ,same as my very first post i get this md5 error again


> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.bz2) MD5Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.bz2) MD5Sum mismatch

after that i tried again with the sudo apt update and upgrade ,i noticed this
> 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

again i dont know if that has something to do with the problem, just felt like adding it just in case

after that i did another gksu update manager command, but get the same error,  failed to fetch due to md5 mismatch

---

### Post by zvacet on 2007-11-22
> You may want to run apt-get update to correct these problems

```
sudo aptitude update
```

---

### Post by n.jin on 2007-11-23
i have tried that command too, still gives me the md5 error for those security packages

now what i have did since its having problems fetching those what i did was i just uncheck the ubuntu 6.06 lts security updates (binary and source) tried tried that gksu update manager and went thru just fine, question is looks like when i go to 6.10 security updates wont be installed, can i just enable those again when iam at edgy to get it updated and hope no md5 error occurs?

thanks again for your time

---

### Post by zvacet on 2007-11-23
Yes,and run

```
sudo aptitude update
```

to update your sourcs list.

---

### Post by n.jin on 2007-11-24
I'd Like to mark this thread as solved, thanks

thanks, i think that did it, thanks for your time zvacet

---

