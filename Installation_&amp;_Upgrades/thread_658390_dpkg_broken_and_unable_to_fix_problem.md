---
title: "dpkg broken and unable to fix problem"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by NuNn DaDdY on 2008-01-04
I was recently upgrading my ubuntu from 6.06 to 6.10 and my computer unexpectedly shutoff in the midst of upgrading.  I am able to restart in ubuntu, however I am notified that I have over 15 packages that are broken and need fixed.  When I attempt to run "dpkg --configure -a" I receive:

dpkg: requested operation requires superuser privilege
corey@NuNn-DaDdY:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x-window-system-core:
 x-window-system-core depends on xorg; however:
  Package xorg is not installed.
dpkg: error processing x-window-system-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...                                               [ ok ]
 * Starting ACPI services... invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.0.4~rc3) | openoffice.org-core-experimental (>> 2.0.4~rc3); however:
  Package openoffice.org-core is not installed.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-core is not installed.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-industrial:
 openoffice.org-style-industrial depends on openoffice.org-common (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-industrial (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-default: openoffice.org-style-default depends on openoffice.org-common (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-default (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-evolution
 x-window-system-core
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-draw
 acpid
 openoffice.org-calc
 acpi-support
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org-style-industrial
 openoffice.org-style-default

Are there any solutions to this problem as I don't have a ubuntu cd handy to reinstall.

---

### Post by Pumalite on 2008-01-04
Run:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
Post results.

---

### Post by NuNn DaDdY on 2008-01-04
Here are the results to the commands you posted:

%sudo dpkg --configure -a

Password:
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x-window-system-core:
 x-window-system-core depends on xorg; however:
  Package xorg is not installed.
dpkg: error processing x-window-system-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...                                               [ ok ]
 * Starting ACPI services... invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.0.4~rc3) | openoffice.org-core-experimental (>> 2.0.4~rc3); however:
  Package openoffice.org-core is not installed.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-core is not installed.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-industrial:
 openoffice.org-style-industrial depends on openoffice.org-common (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-industrial (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-default: openoffice.org-style-default depends on openoffice.org-common (= 2.0.4-0ubuntu7); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-default (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-evolution
 x-window-system-core
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-draw
 acpid
 openoffice.org-calc
 acpi-support
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org-style-industrial
 openoffice.org-style-default


%sudo apt-get update

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Fetched 3B in 1s (3B/s)
Reading package lists... Done


%sudo apt-get upgrade

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-core (> 2.0.2) but it is not installed  openoffice.org-base: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  openoffice.org-calc: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  openoffice.org-common: Depends: openoffice.org-core (> 2.0.4~rc3) but it is not installed or
                                  openoffice.org-core-experimental (> 2.0.4~rc3) but it is not installable
  openoffice.org-draw: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  openoffice.org-evolution: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  openoffice.org-impress: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  openoffice.org-math: Depends: openoffice.org-core (> 2.0.2) but it is not installed
  openoffice.org-writer: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  python-uno: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  x-window-system-core: Depends: xorg but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by Pumalite on 2008-01-04
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
Post results

---

### Post by NuNn DaDdY on 2008-01-04
%sudo apt-get install -f

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-core openoffice.org-help-en-us xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-scalable xorg
Suggested packages:
  xfs xserver
The following NEW packages will be installed:
  openoffice.org-core xorg
The following packages will be upgraded:
  openoffice.org-help-en-us xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-scalable
5 upgraded, 2 newly installed, 0 to remove and 654 not upgraded.
14 not fully installed or removed.
Need to get 0B/57.2MB of archives.
After unpacking 102MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: openoffice.org-help-en-us: dependency problems, but removing anyway as you request:
 language-support-en depends on openoffice.org-help-en-us | openoffice.org2-help-en-us; however:
  Package openoffice.org-help-en-us is to be removed.
  Package openoffice.org2-help-en-us is not installed.
dpkg: error processing openoffice.org-help-en-us (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
corey@NuNn-DaDdY:~$ Errors were encountered while processing:
 openoffice.org-help-en-us


%sudo apt-get update 

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Fetched 3B in 1s (2B/s)
Reading package lists... Done


%sudo apt-get upgrade

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-core (> 2.0.2) but it is not installed  openoffice.org-base: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  openoffice.org-calc: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  openoffice.org-common: Depends: openoffice.org-core (> 2.0.4~rc3) but it is not installed or
                                  openoffice.org-core-experimental (> 2.0.4~rc3) but it is not installable
  openoffice.org-draw: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  openoffice.org-evolution: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  openoffice.org-impress: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  openoffice.org-math: Depends: openoffice.org-core (> 2.0.2) but it is not installed
  openoffice.org-writer: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  python-uno: Depends: openoffice.org-core (= 2.0.4-0ubuntu7) but it is not installed
  x-window-system-core: Depends: xorg but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by Pumalite on 2008-01-04
You are going to have to install openoffice.org2-help-en-us and openoffice.org-core (= 2.0.4-0ubuntu7) before running my commands again.

---

### Post by NuNn DaDdY on 2008-01-04
isn't the command for that :

%sudo apt-get install openoffice.org

---

### Post by Pumalite on 2008-01-04
Yes.
This might be a crucial problem:
'x-window-system-core: Depends: xorg but it is not installed'
Are you having problems with your display?

---

### Post by NuNn DaDdY on 2008-01-05
I'm not really seeing any display problems other than when I click on tabs i.e. administration -> synaptic manager, instead of being highlighted orange it is now just barely highlighted white.

---

### Post by Pumalite on 2008-01-05
What's your status now? Are you able to install programs?

---

### Post by NuNn DaDdY on 2008-01-05
when I tried to run the "sudo apt-get install openoffice.org" I receive the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I manually downloaded the openoffice package by when I try to run the ./setup I receive:

Checksumming...
Extracting ...
./setup: line 226: rpm2cpio: command not found
cpio: premature end of archive
find: usr: No such file or directory
basename: missing operand
Try `basename --help' for more information.
/dev/pts/0
Error: Failed to extract the Java Runtime Environment (JRE) files. (exit code 7)

I have the folder for openoffice located on my desktop, is there somewhere else which I should move it and try to run the ./setup again?

---

### Post by Pumalite on 2008-01-05
3ooka like a reinstall to me unless someone comes with a better idea.

---

### Post by NuNn DaDdY on 2008-01-05
Alrighty thats what I figured I would end up having to do but thank you for your help though.

---

### Post by Pumalite on 2008-01-05
You are welcome. We tried. Good luck.

---

