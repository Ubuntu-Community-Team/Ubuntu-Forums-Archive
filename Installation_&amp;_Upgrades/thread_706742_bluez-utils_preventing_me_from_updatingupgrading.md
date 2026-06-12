---
title: "bluez-utils preventing me from updating/upgrading"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by mwray on 2008-02-24
Below is a log of some of what I have come up against, basically, if I try to update, remove, install, or reinstall bluez-utils (or any-other package) I get this nasty message about bluez-utils:
dpkg: error processing bluez-utils (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bluez-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)

Having followed the instructions, I just get the same error message. I don't even have blue-tooth, nor do I use any of the packages that require bluez-*, and don't know when or why they got installed just because I did an apt-get upgrade, which I though would only upgrade already installed packages...not foist new and broken crap on me...

Version of KUbuntu 7.10, a fairly fresh load, no third party installs, just apt-get update and apt-get upgrade. My understanding is the bluez is gnome specific, which doesn't make sense to me that it installed at all as I have never requested any gnome related packages to be installed...although from looking I see hundreds have been installed just by doing apt-get updates. 

At any rate, does anyone have any idea how to fix this?  I have tried apt-get remove bluez-utils, apt-get -f install, dpkg --configure -a, aptitude install bluez-utils, everything just keeps telling me that bluez-utuils is in a very bad inconsistent state, even if I force it to re-download.  How do I get rid of this nuisance?


mwray@mwray-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  unixodbc odbcinst1debian1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bluez-audio bluez-utils
Suggested packages:
  bluez-firmware
Recommended packages:
  bluez-gnome
The following NEW packages will be installed:
  bluez-audio
The following packages will be upgraded:
  bluez-utils
1 upgraded, 1 newly installed, 0 to remove and 225 not upgraded.
1 not fully installed or removed.
Need to get 0B/462kB of archives.
After this operation, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing bluez-utils (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bluez-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)

mwray@mwray-desktop:~$ sudo dpkg --configure -a
mwray@mwray-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  unixodbc odbcinst1debian1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bluez-audio bluez-utils
Suggested packages:
  bluez-firmware
Recommended packages:
  bluez-gnome
The following NEW packages will be installed:
  bluez-audio
The following packages will be upgraded:
  bluez-utils
1 upgraded, 1 newly installed, 0 to remove and 225 not upgraded.
1 not fully installed or removed.
Need to get 0B/462kB of archives.
After this operation, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing bluez-utils (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bluez-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)
mwray@mwray-desktop:~$
mwray@mwray-desktop:~$ sudo dpkg --configure -a
mwray@mwray-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mwray@mwray-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  unixodbc odbcinst1debian1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bluez-audio bluez-utils
Suggested packages:
  bluez-firmware
Recommended packages:
  bluez-gnome
The following NEW packages will be installed:
  bluez-audio
The following packages will be upgraded:
  bluez-utils
1 upgraded, 1 newly installed, 0 to remove and 225 not upgraded.
1 not fully installed or removed.
Need to get 0B/462kB of archives.
After this operation, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing bluez-utils (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bluez-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)
mwray@mwray-desktop:~$ apt-get --help
apt 0.7.9ubuntu10 for i386 compiled on Feb 13 2008 19:52:13
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove all automatic unused packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
mwray@mwray-desktop:~$ man apt-get
man: can't set the locale; make sure $LC_* and $LANG are correct
mwray@mwray-desktop:~$ sudo apt-get --reinstall bluez-utils
E: Invalid operation bluez-utils
mwray@mwray-desktop:~$ sudo apt-get --reinstall
apt 0.7.9ubuntu10 for i386 compiled on Feb 13 2008 19:52:13
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove all automatic unused packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
mwray@mwray-desktop:~$ man apt-get
man: can't set the locale; make sure $LC_* and $LANG are correct
mwray@mwray-desktop:~$ sudo apt-get --reinstall -f install bluez-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bluez-utils: Depends: bluez-audio but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mwray@mwray-desktop:~$ sudo apt-get --reinstall -f install bluez-utils bluez-audio
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  unixodbc odbcinst1debian1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  bluez-firmware
Recommended packages:
  bluez-gnome
The following NEW packages will be installed:
  bluez-audio
The following packages will be upgraded:
  bluez-utils
1 upgraded, 1 newly installed, 0 to remove and 225 not upgraded.
1 not fully installed or removed.
Need to get 0B/462kB of archives.
After this operation, 32.8kB of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing bluez-utils (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bluez-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)
mwray@mwray-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  unixodbc odbcinst1debian1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bluez-audio bluez-utils
Suggested packages:
  bluez-firmware
Recommended packages:
  bluez-gnome
The following NEW packages will be installed:
  bluez-audio
The following packages will be upgraded:
  bluez-utils
1 upgraded, 1 newly installed, 0 to remove and 225 not upgraded.
1 not fully installed or removed.
Need to get 0B/462kB of archives.
After this operation, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing bluez-utils (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bluez-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)
mwray@mwray-desktop:~$

---

### Post by Pumalite on 2008-02-24
You might want to try:
sudo dpkg --remove --force-remove-reinstreq bluez-utils bluez-audio
And then reinstall

---

### Post by soumyasutar on 2008-02-28
Hi , 
I am new to ubuntu 7.10 and BlueZ world.
I want to bring up BlueZ.Just now i install ubuntu 7.10 from Live Cd.
Can you pl show me the pointer, so that i can bring up BlueZ in ubuntu 7.10 and do some experiment on it.

Thanks-N-Regards,
Soumya

---

