---
title: "trouble installing network-manager-openvpn / emacs issue"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by annec on 2010-10-04
Hi all,

It's been a while since I meant to resolve this emacs-related issue when installing basically any package. 

Since I really need network-manager-openvpn, I decided to finally try and ask. 

This is a known bug I believe, with no fix if I understand well. My question is: is there a way to go around it (instead of fixing it)

Here it goes : when installing a package (in this case, network-manager-openvpn), emacs gets in the way like this: 

```
root@AC:/home/ac# apt-get install network-manager-openvpn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-openvpn is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up emacs22 (22.2-0ubuntu9) ...
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs22 failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs22
!! and attach the file /tmp/emacs22.mrK2gG
dpkg: error processing emacs22 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up emacs22-gtk (22.2-0ubuntu9) ...
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs22 failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs22
!! and attach the file /tmp/emacs22.fGEZHV
dpkg: error processing emacs22-gtk (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up emacs22-nox (22.2-0ubuntu9) ...
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs22 failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs22
!! and attach the file /tmp/emacs22.SmUFHI
dpkg: error processing emacs22-nox (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up emacs23-lucid (23.1+1-4ubuntu7) ...
emacs-install emacs23
install/dictionaries-common: Byte-compiling for emacsen flavour emacs23
.: 1172: Can't open /usr/local/bin/update/install/mapname.sh
emacs-install: /usr/lib/emacsen-common/packages/install/dictionaries-common emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 2.
dpkg: error processing emacs23-lucid (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 emacs22
 emacs22-gtk
 emacs22-nox
 emacs23-lucid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And the package is not installed. 

I have already tried uninstalling emacs. Doesn't work...

Is there anything I can do? I've been googling and googling about that, so I am sorry if I missed a post or any solution and I am still asking. If so, I'd love a link!

Thank you so much in advance!

AC

---

### Post by annec on 2010-10-04
Hi again,

Answering myself, partly...

A complete removal of all emacs-related packages solved the issue. I thought I had tried that already. But apparently I had not done it right.  

However, reinstalling emacs does not work. Still the same messages:

```
root@AC:/home/ac# apt-get install emacs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  emacs23 emacs23-bin-common emacs23-common emacsen-common
Suggested packages:
  emacs23-el
The following NEW packages will be installed:
  emacs emacs23 emacs23-bin-common emacs23-common emacsen-common
0 upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
Need to get 3,079kB/23.9MB of archives.
After this operation, 73.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://fr.archive.ubuntu.com/ubuntu/ lucid/main emacsen-common 1.4.19ubuntu1 [19.0kB]
Get:2 http://fr.archive.ubuntu.com/ubuntu/ lucid/main emacs23 23.1+1-4ubuntu7 [3,038kB]
Get:3 http://fr.archive.ubuntu.com/ubuntu/ lucid/main emacs 23.1+1-4ubuntu7 [22.1kB]
Fetched 3,079kB in 4s (619kB/s)
Selecting previously deselected package emacsen-common.
(Reading database ... 393447 files and directories currently installed.)
Unpacking emacsen-common (from .../emacsen-common_1.4.19ubuntu1_all.deb) ...
Selecting previously deselected package emacs23-common.
Unpacking emacs23-common (from .../emacs23-common_23.1+1-4ubuntu7_all.deb) ...
Selecting previously deselected package emacs23-bin-common.
Unpacking emacs23-bin-common (from .../emacs23-bin-common_23.1+1-4ubuntu7_i386.deb) ...
Selecting previously deselected package emacs23.
Unpacking emacs23 (from .../emacs23_23.1+1-4ubuntu7_i386.deb) ...
Selecting previously deselected package emacs.
Unpacking emacs (from .../emacs_23.1+1-4ubuntu7_all.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up emacsen-common (1.4.19ubuntu1) ...
emacsen-common: Handling install of emacsen flavor emacs

Setting up emacs23-common (23.1+1-4ubuntu7) ...
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package emacs23-common should be rebuilt with new debhelper to get trigger support

Setting up emacs23-bin-common (23.1+1-4ubuntu7) ...
update-alternatives: using /usr/bin/b2m.emacs23 to provide /usr/bin/b2m (b2m) in auto mode.
update-alternatives: using /usr/bin/ctags.emacs23 to provide /usr/bin/ctags (ctags) in auto mode.
update-alternatives: using /usr/bin/ebrowse.emacs23 to provide /usr/bin/ebrowse (ebrowse) in auto mode.
update-alternatives: using /usr/bin/emacsclient.emacs23 to provide /usr/bin/emacsclient (emacsclient) in auto mode.
update-alternatives: using /usr/bin/etags.emacs23 to provide /usr/bin/etags (etags) in auto mode.
update-alternatives: using /usr/bin/grep-changelog.emacs23 to provide /usr/bin/grep-changelog (grep-changelog) in auto mode.
update-alternatives: using /usr/bin/rcs-checkin.emacs23 to provide /usr/bin/rcs-checkin (rcs-checkin) in auto mode.

Setting up emacs23 (23.1+1-4ubuntu7) ...
update-alternatives: using /usr/bin/emacs23-x to provide /usr/bin/emacs (emacs) in auto mode.
emacs-install emacs23
install/dictionaries-common: Byte-compiling for emacsen flavour emacs23
.: 1172: Can't open /usr/local/bin/update/install/mapname.sh
emacs-install: /usr/lib/emacsen-common/packages/install/dictionaries-common emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 2.
dpkg: error processing emacs23 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs23 | emacs23-lucid | emacs23-nox; however:
  Package emacs23 is not configured yet.
  Package emacs23-lucid which provides emacs23 is not installed.
  Package emacs23-lucid is not installed.
  Package emacs23-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 emacs23
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 

Well, at least I was able to install my so-much-wanted network-manager-openvpn !

Anyway, the emacs issue is still there. I keep this thread open in case someone knows how to fix it... I'll look into it some more, after getting some sleep...



AC

---

### Post by annec on 2010-10-04
I should add that 
apt-get install emacs23-lucid

or

apt-get install emacs23-nox 

both return dependency errors too.

That's it for tonight, but like I said, I would be interested in any solution!

AC

---

