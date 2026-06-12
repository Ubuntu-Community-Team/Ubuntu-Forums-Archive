---
title: "Installing mythtv fails due to dependency failures"
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by harlan@bloomenterprises.o on 2013-08-01
Hello,
  I'm trying to install mythtv on Ubuntu 12.04.  All my patches are up to date.  I did an update and upgrade, did not fix the problem.  I even tried to repair the package system; still no go.

  Below is my install command and output.  Please let me know if you need any more information.

Thank You for your assistance!

Harlan...

```
# aptitude install mythtv-backend
The following NEW packages will be installed:
  aspell{a} aspell-en{a} dictionaries-common{a} enchant{a} libenchant1c2a{a} libmyth-python{a} libmythtv-perl{a} libnet-upnp-perl{a} 
  libwebkitgtk-3.0-0{a} mythtv-backend mythtv-transcode-utils{a} python-urlgrabber{a} zenity{a} 
0 packages upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.3 MB of archives. After unpacking 33.8 MB will be used.
Do you want to continue? [Y/n/?] y
Get: 1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main dictionaries-common all 1.12.1ubuntu2 [246 kB]
Get: 2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main aspell amd64 0.60.7~20110707-1 [92.5 kB]
Get: 3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main aspell-en all 6.0-0-6ubuntu2 [250 kB]
Get: 4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libenchant1c2a amd64 1.6.0-7 [79.4 kB]
Get: 5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main enchant amd64 1.6.0-7 [13.5 kB]
Get: 6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main python-urlgrabber all 3.9.1-4ubuntu2 [48.5 kB]
Get: 7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse libmyth-python all 2:0.25.2+fixes.20120802.46cab93-0ubuntu1 [353 kB]
Get: 8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libnet-upnp-perl all 1.4.2-1 [54.7 kB]
Get: 9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse libmythtv-perl all 2:0.25.2+fixes.20120802.46cab93-0ubuntu1 [50.4 kB]
Get: 10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libwebkitgtk-3.0-0 amd64 1.8.3-0ubuntu0.12.04.1 [7,118 kB]
Get: 11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse mythtv-transcode-utils amd64 2:0.25.2+fixes.20120802.46cab93-0ubuntu1 [191 kB]
Get: 12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main zenity amd64 3.4.0-0ubuntu4 [65.1 kB]                                               
Get: 13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse mythtv-backend amd64 2:0.25.2+fixes.20120802.46cab93-0ubuntu1 [1,692 kB]      
Fetched 10.3 MB in 43s (234 kB/s)                                                                                                                     
Preconfiguring packages ...
Selecting previously unselected package dictionaries-common.
(Reading database ... 451439 files and directories currently installed.)
Unpacking dictionaries-common (from .../dictionaries-common_1.12.1ubuntu2_all.deb) ...
Adding 'diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common'
Selecting previously unselected package aspell.
Unpacking aspell (from .../aspell_0.60.7~20110707-1_amd64.deb) ...
Selecting previously unselected package aspell-en.
Unpacking aspell-en (from .../aspell-en_6.0-0-6ubuntu2_all.deb) ...
Selecting previously unselected package libenchant1c2a.
Unpacking libenchant1c2a (from .../libenchant1c2a_1.6.0-7_amd64.deb) ...
Selecting previously unselected package enchant.
Unpacking enchant (from .../enchant_1.6.0-7_amd64.deb) ...
Selecting previously unselected package python-urlgrabber.
Unpacking python-urlgrabber (from .../python-urlgrabber_3.9.1-4ubuntu2_all.deb) ...
Selecting previously unselected package libmyth-python.
Unpacking libmyth-python (from .../libmyth-python_2%3a0.25.2+fixes.20120802.46cab93-0ubuntu1_all.deb) ...
Selecting previously unselected package libnet-upnp-perl.
Unpacking libnet-upnp-perl (from .../libnet-upnp-perl_1.4.2-1_all.deb) ...
Selecting previously unselected package libmythtv-perl.
Unpacking libmythtv-perl (from .../libmythtv-perl_2%3a0.25.2+fixes.20120802.46cab93-0ubuntu1_all.deb) ...
Selecting previously unselected package libwebkitgtk-3.0-0.
Unpacking libwebkitgtk-3.0-0 (from .../libwebkitgtk-3.0-0_1.8.3-0ubuntu0.12.04.1_amd64.deb) ...
Selecting previously unselected package mythtv-transcode-utils.
Unpacking mythtv-transcode-utils (from .../mythtv-transcode-utils_2%3a0.25.2+fixes.20120802.46cab93-0ubuntu1_amd64.deb) ...
Selecting previously unselected package zenity.
Unpacking zenity (from .../zenity_3.4.0-0ubuntu4_amd64.deb) ...
Selecting previously unselected package mythtv-backend.
Unpacking mythtv-backend (from .../mythtv-backend_2%3a0.25.2+fixes.20120802.46cab93-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
/usr/bin/mandb: iconv_open ("UTF-8//IGNORE", "ISO-8859-1"): Invalid argument
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Setting up dictionaries-common (1.12.1ubuntu2) ...
Unsupported conversion from iso-8859-1 to utf8: Invalid argument at /usr/share/perl5/Debian/DictionariesCommon.pm line 492, <DICT> line 4.
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 22
dpkg: dependency problems prevent configuration of aspell:
 aspell depends on dictionaries-common (>> 0.40); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing aspell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aspell-en:
 aspell-en depends on aspell (>= 0.60.3-2); however:
  Package aspell is not configured yet.
 aspell-en depends on dictionaries-common (>= 0.49.2); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing aspell-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libenchant1c2a:
 libenchant1c2a depends on aspell-en | myspell-dictionary | aspell-dictionary | ispell-dictionary | hunspell-dictionary; however:
  Package aspell-en is not configured yet.
  PackagNo apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                                                                                                    No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                                                                                                          No apport report written because MaxReports is reached already
                  e myspell-dictionary is not installed.
  Package aspell-dictionary is not installed.
  Package aspell-en which provides aspell-dictionary is not configured yet.
  Package ispell-dictionary is not installed.
  Package hunspell-dictionary is not installed.
dpkg: error processing libenchant1c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of enchant:
 enchant depends on libenchant1c2a (>= 1.6); however:
  Package libenchant1c2a is not configured yet.
dpkg: error processing enchant (--configure):
 dependency problems - leaving unconfigured
Setting up python-urlgrabber (3.9.1-4ubuntu2) ...
Setting up libmyth-python (2:0.25.2+fixes.20120802.46cab93-0ubuntu1) ...
Setting up libnet-upnp-perl (1.4.2-1) ...
Setting up libmythtv-perl (2:0.25.2+fixes.20120802.46cab93-0ubuntu1) ...
dpkg: dependency problems prevent configuration of libwebkitgtk-3.0-0:
 libwebkitgtk-3.0-0 depends on libenchant1c2a (>= 1.6); however:
  Package libenchant1c2a is not configured yet.
dpkg: error processing libwebkitgtk-3.0-0 (--configure):
 dependency problems - leaving unconfigured
Setting up mythtv-transcode-utils (2:0.25.2+fixes.20120802.46cab93-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of zenity:
 zenity depends on libwebkitgtk-3.0-0 (>= 1.3.10); however:
  Package libwebkitgtk-3.0-0 is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on zenity | kdebase-bin; however:
  Package zenity is not configured yet.
  Package kdebase-bin is not installed.
dpkg: error processing mythtv-backend (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 dictionaries-common
 aspell
 aspell-en
 libenchant1c2a
 enchant
 libwebkitgtk-3.0-0
 zenity
 mythtv-backend
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up dictionaries-common (1.12.1ubuntu2) ...
Unsupported conversion from iso-8859-1 to utf8: Invalid argument at /usr/share/perl5/Debian/DictionariesCommon.pm line 492, <DICT> line 4.
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 22
dpkg: dependency problems prevent configuration of aspell:
 aspell depends on dictionaries-common (>> 0.40); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing aspell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aspell-en:
 aspell-en depends on aspell (>= 0.60.3-2); however:
  Package aspell is not configured yet.
 aspell-en depends on dictionaries-common (>= 0.49.2); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing aspell-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libenchant1c2a:
 libenchant1c2a depends on aspell-en | myspell-dictionary | aspell-dictionary | ispell-dictionary | hunspell-dictionary; however:
  Package aspell-en is not configured yet.
  Package myspell-dictionary is not installed.
  Package aspell-dictionary is not installed.
  Package aspell-en which provides aspell-dictionary is not configured yet.
  Package ispell-dictionary is not installed.
  Package hunspell-dictionary is not installed.
dpkg: error processing libenchant1c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of enchant:
 enchant depends on libenchant1c2a (>= 1.6); however:
  Package libenchant1c2a is not configured yet.
dpkg: error processing enchant (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwebkitgtk-3.0-0:
 libwebkitgtk-3.0-0 depends on libenchant1c2a (>= 1.6); however:
  Package libenchant1c2a is not configured yet.
dpkg: error processing libwebkitgtk-3.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on libwebkitgtk-3.0-0 (>= 1.3.10); however:
  Package libwebkitgtk-3.0-0 is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on zenity | kdebase-bin; however:
  Package zenity is not configured yet.
  Package kdebase-bin is not installed.
dpkg: error processing mythtv-backend (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dictionaries-common
 aspell
 aspell-en
 libenchant1c2a
 enchant
 libwebkitgtk-3.0-0
 zenity
 mythtv-backend
```

---

### Post by TheFu on 2013-08-01
When I look through the messages, I ask - did he install any .deb files outside the repositories or add any extra non-Canonical repos?  Going "off the reservation" is a common way to get into dependency issues.

After looking through the listed repositories in your command, it looks like you probably did not use outside Canonical repos.  Any straight .deb package installs?

---

### Post by harlan@bloomenterprises.o on 2013-08-01
I added NX Server and associated .deb files years ago, Virtualbox I keep updated from Sun/Oracle and I had Plex installed.  I've since removed Plex.

With all of these, I've had no problems keeping programs and OS updated using the package manager.  I ran Plex with MythTV for quite a while without any problems.

I had some drive failures and redoing other drives.  To that end I needed to drop the mythconv database, and others, and it seemed like a good time to make some changes.  Now I can't get packages to install properly.

I have several VM's running nearly all the time, hence using Virtualbox.  At the moment however, none of the VM's are running, neither is Virtualbox.

I've searched online for things to try, including doing a clean of the package system.  So far, nothing has worked and I'm looking for ideas.

Thank You for your help!

---

### Post by TheFu on 2013-08-02
Sorry to say this but those external programs installed via **dpkg **are the likely cause.  Eventually, the package manager gets into a state that cannot be resolved.  I can only guess that if you de-install those .deb installed packages, then the package manager will not have conflicting dependencies.

In order of "badness"
* source code - you are now the manual package manager and update guy.
* .deb packages - you are now the update guy.
* PPA - do you really trust the PPA owner to never make a mistake and always update to support whatever kernel version you happen to be runnnig AND keep up with any package updates in the core libraries?
* Non-Canonical repo - Same as PPA.  I use a PPA from OpenSUSE for a complex tool. It scares me. I expect the APT DB dependencies to be screwed eventually.
* Canonical repos. People make mistakes, but I use **apt-get dist-upgrade** weekly.

NX is part of the Ubuntu repos now.
You are better than me - never got MythTV to work, but I never had a supported tuner card and couldn't figure out how to install it without any tuner.  XBMC is what I run on an AMD E350 box.  I'm looking at Plex now that I've been forced to get a Roku (Amazon Prime streaming stopped working for me on Ubuntu in May).

KVM is part of the kernel and obviously part of the Canonical repositories. Just a thought.

**Virtualization .... **
VirtualBox is fantastic for desktop-on-desktop VMs.  For servers, KVM is lighter and extremely stable. I've never had a crash of any sort since switching to KVM.  VirtualBox locked up the entire machine a few times.  I've been running virtualbox and kvm and xen and ESXi for many, many years.  I still use VirtualBox on MS-Windows, but everything else has been converted to KVM - even my daily use desktop.  I'm actually connected to the desktop from a Win7 laptop over an NX remote desktop connection right now. I've connected to the same desktop from around the world --- literally - around the world.  Of course, it works best on the same GigE LAN, but it works pretty well from different continents like Africa, Asia, Europe, South America, Central America too. It isn't perfect, but for office productivity apps and programming, the convenience is fantastic.  You already know how great NX is - no need to preach. This is all for lurkers.

BTW, I have a 10.04 server (no GUI) that is in the same .deb package management hell and has been for a few months. It isn't on the internet and I have plans to migrate everything off it, then reinstall everything with 12.04.x LTS.  It is THE main storage server here, so taking it down for more than a few hours is not an option. It has multiple disk arrays connected, and internal web services, backups, ... the list goes on and on. Just wanted to share that - I don't have all the answers and struggle with the same issues everyone else here does from time to time.

I hope someone smarted than me responds with a real solution or that you (smarter than me too!) find it and post back.  It would be much easier to upgrade the 10.04 box to 12.04 than to start over from scratch.

Thanks for YOUR help as well!

---

