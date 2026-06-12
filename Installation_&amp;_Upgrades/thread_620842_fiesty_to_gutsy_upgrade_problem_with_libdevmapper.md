---
title: "fiesty to gutsy upgrade problem with libdevmapper"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by tjbonzo on 2007-11-23
While trying to upgrade form Fiesty to Gutsy - I get an error in /var/log/dist-upgrade/main.log complaining about a libdevmapper1.02.1 dependency problem. When I try to do an install of libdevmapper1.02.1 with gutsy repository it complains. Any hints around this problem?

2007-11-23 01:39:49,513 DEBUG demoted: 'binfmt-support emacs21-bin-common emacs21-common emacs21-nox feisty-session-splashes festlex-cmu festlex-poslex festvox-kallpc16k gcj-4.1-base gij-4.1 gnome-cups-manager libdb3 libgda2-3 libgda2-common libglib1.2 libgnomecupsui1.0-1c2a libgtk1.2 libgtk1.2-common liblzo1 libportaudio0 libslab0 libstlport5.1 libxml1 libxmlsec1 libxmlsec1-nss libxmlsec1-openssl openoffice.org-filter-mobiledev pmount ttf-baekmuk vnc-common xmms xvncviewer'
2007-11-23 01:40:15,178 DEBUG Installing 'libdevmapper1.02.1' (priority in required set 'required' but not scheduled for install)
2007-11-23 01:40:29,939 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
root@bonzopad:/var/log/dist-upgrade# update-manager 
warning: could not initiate dbus
extracting '/tmp/tmpOCHz5m/gutsy.tar.gz'
authenticate '/tmp/tmpOCHz5m/gutsy.tar.gz' against '/tmp/tmpOCHz5m/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
 

# apt-get -s install libdevmapper1.02.1Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libdevmapper1.02.1: Depends: libselinux1 (>= 2.0.15) but 1.32-3ubuntu1 is to be installed
                      Depends: libsepol1 (>= 2.0.3) but 1.14-2build1 is to be installed
E: Broken packages


grep gutsy /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

---

### Post by zvacet on 2007-11-23
**synaptic>edit>fix broken packages**

---

### Post by tjbonzo on 2007-11-23
Thanks - but the problem is **during** the upgrade - so I get the "cannot calculate upgrade" message and my sources.list reverts back to the feisty source. Feisty isn't requiring libdevmapper1.02.1  (it only has libdevmapper1.02 ) - apparently gutsy needs the 1.02.1 version which has broken dependencies.

---

### Post by tjbonzo on 2007-11-25
Solved my own problem - so in case this helps someone else - I had my fiesty installation with some gutsy pinning - i.e. /etc/apt/preferences had:


[INDENT]# cat preferences.1124 
Package: *
Pin: release a=fiesty
Pin-Priority: 700

Package: *
Pin: release a=gutsy
Pin-Priority: 60[/INDENT]

I got rid of the last package ( a=gutsy) and the upgrade worked fine.

---

