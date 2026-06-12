---
title: "Can't update/install"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by teocomi on 2011-03-30
Hello, I have Ubuntu 10.10, Software Center does not work, and it always shows up errors. When I run:

```
dpkg --configure -a
```

I get:

```


Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 98, in <module>
    os.remove(os.path.join(defaults_dest,f))
OSError: [Errno 21] Is a directory: '/var/lib/gconf/defaults/apps'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.4.6-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-btdownload:
 gnome-btdownload depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-btdownload (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsyncdaemon-1.0-1:
 libsyncdaemon-1.0-1 depends on ubuntuone-client (>= 1.4.6-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing libsyncdaemon-1.0-1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
 ubuntuone-client
 software-center
 ubuntuone-client-gnome
 gnome-btdownload
 gnome-screensaver
 libsyncdaemon-1.0-1


```

What does this mean? What can I do? 
Thanks!

---

### Post by tommcd on 2011-03-31
Open a terminal and run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Does that update the system ok? If not, then post the errors here.
Also post the contents of your */etc/apt/sources.list*.

---

### Post by teocomi on 2011-03-31
Thanks, excuse me but I'm really new to Linux systems... These are the errors:

```


root@NAS:~# apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/team-iquik/alsa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/team-iquik/alsa/ubuntu/ maverick/main Translation-en_US
Hit http://it.archive.ubuntu.com maverick Release.gpg
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge Release.gpg
Ign http://webmin.mirror.somersettechsolutions.co.uk/repository/ sarge/contrib Translation-en
Ign http://webmin.mirror.somersettechsolutions.co.uk/repository/ sarge/contrib Translation-en_US
Hit http://extras.ubuntu.com maverick Release
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/team-xbmmc/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/team-xbmmc/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Hit http://security.ubuntu.com maverick-security Release
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge Release
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib amd64 Packages
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://ppa.launchpad.net maverick Release
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib amd64 Packages
Hit http://download.webmin.com sarge Release.gpg
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://ppa.launchpad.net maverick/main Sources
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib amd64 Packages
Ign http://ppa.launchpad.net maverick/main Sources
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main Sources
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main Sources
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://download.webmin.com/download/repository/ sarge/contrib Translation-en
Ign http://download.webmin.com/download/repository/ sarge/contrib Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://it.archive.ubuntu.com maverick-updates Release.gpg
Hit http://download.webmin.com sarge Release
Ign http://download.webmin.com sarge/contrib amd64 Packages
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://download.webmin.com sarge/contrib amd64 Packages
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://download.webmin.com sarge/contrib amd64 Packages
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://it.archive.ubuntu.com maverick Release
Hit http://it.archive.ubuntu.com maverick-updates Release
Hit http://it.archive.ubuntu.com maverick/main Sources
Hit http://it.archive.ubuntu.com maverick/restricted Sources
Hit http://it.archive.ubuntu.com maverick/universe Sources
Hit http://it.archive.ubuntu.com maverick/multiverse Sources
Hit http://it.archive.ubuntu.com maverick/main amd64 Packages
Hit http://it.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://it.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://it.archive.ubuntu.com maverick/multiverse amd64 Packages
Hit http://it.archive.ubuntu.com maverick-updates/main Sources
Hit http://it.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://it.archive.ubuntu.com maverick-updates/universe Sources
Hit http://it.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://it.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://it.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://it.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://it.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
W: Failed to fetch http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmmc/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmmc/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

```

root@NAS:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gdm webmin
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 15.6MB of archives.
After this operation, 782kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://it.archive.ubuntu.com/ubuntu/ maverick-updates/main gdm amd64 2.30.5-0ubuntu4.1 [809kB]
Get:2 http://download.webmin.com/download/repository/ sarge/contrib webmin all 1.540 [14.8MB]
Fetched 15.6MB in 11s (1,348kB/s)
Preconfiguring packages ...
(Reading database ... 232847 files and directories currently installed.)
Preparing to replace webmin 1.530 (using .../archives/webmin_1.540_all.deb) ...
Unpacking replacement webmin ...
Preparing to replace gdm 2.30.5-0ubuntu4 (using .../gdm_2.30.5-0ubuntu4.1_amd64.deb) ...
Unpacking replacement gdm ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 98, in <module>
    os.remove(os.path.join(defaults_dest,f))
OSError: [Errno 21] Is a directory: '/var/lib/gconf/defaults/apps'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-btdownload:
 gnome-btdownload depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-btdownload (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsyncdaemon-1.0-1:
 libsyncdaemon-1.0-1 depends on ubuntuone-client (>= 1.4.6-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.No apport report written because the error message indicates its a followup error from a previous failure.
                                                                           No apport report written because the error message indicates its a followup error from a previous failure.
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already

dpkg: error processing libsyncdaemon-1.0-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on libsyncdaemon-1.0-1; however:
  Package libsyncdaemon-1.0-1 is not configured yet.
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.4.6-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
Setting up webmin (1.540) ...
Webmin install complete. You can now login to https://NAS:10000/
as root with your root password, or as any user who can use sudo
to run commands as root.
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 gconf2
 gnome-btdownload
 gnome-screensaver
 ubuntuone-client
 libsyncdaemon-1.0-1
 ubuntuone-client-gnome
 software-center
 gdm
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

And here source.list

```


root@NAS:~# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://it.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://it.archive.ubuntu.com/ubuntu/ maverick universe
deb http://it.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://it.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://it.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib



```

---

### Post by tommcd on 2011-03-31
From your *sources.list*:
```
deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib
```
Why do you have Debian Sarge mirrors on Ubuntu 10.10? This is guaranteed to cause you problems. Remove the Sarge repos and then run:```
sudo apt-get update
sudo apt-get dist-upgrade
```
And see if you can update the system.

Also, your output of: ```
apt-get update
``` lists a lot of PPA repos that do not seem to be in your *sources.list*. They must be in your */etc/apt/sources.list.d/* directory.
If removing the Sarge repos does not fix things, then I would remove the PPA repos as well. You are getting 404 errors on some of those PPA repos anyway.

Are you running the system as root? You should not be. Enabling the root account in Ubuntu is not recommended.

---

### Post by teocomi on 2011-04-01
Hi tommcd, I did remove the Debian Sarge mirrors (I guess I did add them by mistake while trying to install webmin), and also I removed all the repos in /etc/apt/sources.list.d/.

Now *apt-get update* does not show errors, but *sudo apt-get dist-upgrade* still yes:

```


teocomi@NAS:/etc/apt/sources.list.d$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 98, in <module>
    os.remove(os.path.join(defaults_dest,f))
OSError: [Errno 21] Is a directory: '/var/lib/gconf/defaults/apps'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-btdownload:
 gnome-btdownload depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-btdownload (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency pNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                       No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                       No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                                                                                                         No apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                                                                                                           No apport report written because MaxReports is reached already
                                               roblems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsyncdaemon-1.0-1:
 libsyncdaemon-1.0-1 depends on ubuntuone-client (>= 1.4.6-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing libsyncdaemon-1.0-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on libsyncdaemon-1.0-1; however:
  Package libsyncdaemon-1.0-1 is not configured yet.
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.4.6-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
 gdm
 gnome-btdownload
 gnome-screensaver
 ubuntuone-client
 libsyncdaemon-1.0-1
 ubuntuone-client-gnome
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks for the great help!

P.S.
I'm not using the system as root, I just sometimes do 
*sudo -s* at the beginning of my session.. I this ok?

---

### Post by tommcd on 2011-04-01
> **teocomi said:**
> 
Now *apt-get update* does not show errors, but *sudo apt-get dist-upgrade* still yes: ...
Well if you ran updates with that sarge repo in there, you may have mutated parts of your system into Debian sarge. Try this:
```
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
Sudo apt-get upgrade

```
If that does not fix things, then try: 
```
sudo dpkg --clear-avail && sudo apt-get update
sudo apt-get dist-upgrade
```
If you get errors from those, then post them here.
Also try opening Synaptic and select "Custom Filters" and select the filter for broken packages. See if it shows broken packages and allows you to fix them. 
> **teocomi said:**
> 
I'm not using the system as root, I just sometimes do 
*sudo -s* at the beginning of my session.. I this ok?
Yes, this should be ok as far as I know. I just use sudo though.

---

### Post by teocomi on 2011-04-02
Argh, damn sarge repos! Still is't reporting errors:

```

teocomi@NAS:~$ sudo dpkg --clear-avail && sudo apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Hit http://extras.ubuntu.com maverick Release
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Hit http://it.archive.ubuntu.com maverick Release.gpg
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://it.archive.ubuntu.com maverick-updates Release.gpg
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://it.archive.ubuntu.com maverick Release
Hit http://it.archive.ubuntu.com maverick-updates Release
Hit http://it.archive.ubuntu.com maverick/main Sources
Hit http://it.archive.ubuntu.com maverick/restricted Sources
Hit http://it.archive.ubuntu.com maverick/universe Sources
Hit http://it.archive.ubuntu.com maverick/multiverse Sources
Hit http://it.archive.ubuntu.com maverick/main amd64 Packages
Hit http://it.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://it.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://it.archive.ubuntu.com maverick/multiverse amd64 Packages
Hit http://it.archive.ubuntu.com maverick-updates/main Sources
Hit http://it.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://it.archive.ubuntu.com maverick-updates/universe Sources
Hit http://it.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://it.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://it.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://it.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://it.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Reading package lists... Done

```


```

teocomi@NAS:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 98, in <module>
    os.remove(os.path.join(defaults_dest,f))
OSError: [Errno 21] Is a directory: '/var/lib/gconf/defaults/apps'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-btdownload:
 gnome-btdownload depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-btdownload (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency pNo apport report written because the error message indicates its a followup error from a previous failure.
                                       No apport report written because the error message indicates its a followup error from a previous failure.
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       roblems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsyncdaemon-1.0-1:
 libsyncdaemon-1.0-1 depends on ubuntuone-client (>= 1.4.6-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing libsyncdaemon-1.0-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on libsyncdaemon-1.0-1; however:
  Package libsyncdaemon-1.0-1 is not configured yet.
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.4.6-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
 gdm
 gnome-btdownload
 gnome-screensaver
 ubuntuone-client
 libsyncdaemon-1.0-1
 ubuntuone-client-gnome
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks for all the help!

---

### Post by tommcd on 2011-04-03
You could try reinstalling gconf2:
```
sudo apt-get install --reinstall gconf2
```
I don't know if this will help though; but it can't hurt.
Using that Debian repo has caused you some awful dependency problems here. 
What is your output of: ```
apt-cache policy gconf2
```
The current version of gconf2 in 10.10 is 2.31.91:
```

tom@desktop1:/data$ apt-cache policy gconf2
gconf2:
  Installed: 2.31.91-0ubuntu3.1
  Candidate: 2.31.91-0ubuntu3.1
  Version table:
 *** 2.31.91-0ubuntu3.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2.31.91-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/main i386 Packages

```

Also, try purging gnome-btdownload and webmin:
```
sudo apt-get remove --purge gnome-btdownload webmin
```
The gnome-btdownload package seems to be causing you problems. I do not have that on my system, so it is not an essential package.
And webmin is nowhere to be found on the default 10.10 repos.

---

### Post by teocomi on 2011-04-03
No way, it's still the same:

```

teocomi@NAS:~$ sudo apt-get install --reinstall gconf2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu-xdg libjpeg8 lxmusic lxde-icon-theme libjpeg-progs lxappearance obconf
  libio-pty-perl leafpad lxde-common libauthen-pam-perl lxrandr pcmanfm
  libmenu-cache1 lxde-core arj xmms2-plugin-id3v2 lxsession-edit libfm-gtk0
  apt-show-versions lxinput lxmenu-data xmms2-plugin-alsa libfm0
  libxmmsclient6 xmms2-core gpicview xmms2-plugin-vorbis libxmmsclient-glib1
  lxshortcut lxpanel xmms2-plugin-mad libapt-pkg-perl xscreensaver xarchiver
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 98, in <module>
    os.remove(os.path.join(defaults_dest,f))
OSError: [Errno 21] Is a directory: '/var/lib/gconf/defaults/apps'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-btdownload:
 gnome-btdownload depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-btdownload (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency pNo apport report written because the error message indicates its a followup error from a previous failure.
                                       No apport report written because the error message indicates its a followup error from a previous failure.
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       roblems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsyncdaemon-1.0-1:
 libsyncdaemon-1.0-1 depends on ubuntuone-client (>= 1.4.6-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing libsyncdaemon-1.0-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on libsyncdaemon-1.0-1; however:
  Package libsyncdaemon-1.0-1 is not configured yet.
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.4.6-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
 gdm
 gnome-btdownload
 gnome-screensaver
 ubuntuone-client
 libsyncdaemon-1.0-1
 ubuntuone-client-gnome
 software-center

```

But gconf2 looks fine though.. :confused:

```



teocomi@NAS:~$ apt-cache policy gconf2
gconf2:
  Installed: 2.31.91-0ubuntu3.1
  Candidate: 2.31.91-0ubuntu3.1
  Version table:
 *** 2.31.91-0ubuntu3.1 0
        500 http://it.archive.ubuntu.com/ubuntu/ maverick-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.31.91-0ubuntu3 0
        500 http://it.archive.ubuntu.com/ubuntu/ maverick/main amd64 Packages

```

---

### Post by tommcd on 2011-04-03
At this point I do not know what else you could do.
If I can find anything else I will report back.

---

### Post by teocomi on 2011-04-03
Thanks a lot, you've been very nice! Maybe if I get the time I will opt for a new installation...

---

### Post by lekonna on 2011-04-12
i've got the same problem here. removed python and re-installed ubuntu-desktop, still complains a lot.

---

### Post by lekonna on 2011-04-12
seems to be related to the fact that i seem to have python installed in 2 places in the system and dpkg might be using the wrong one, how do i check or change which python installation the dpkg uses ?

---

