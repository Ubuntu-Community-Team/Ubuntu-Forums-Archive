---
title: "Can't install kGuitar + sound playback problem"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by Edrihan on 2009-12-16
I'm a very recent convert to linux, and have been equally impressed and aggravated during my short stint so far. I understand that there is a learning curve and that with more knowledge will come more ease. Most of what I've done so far has been straightforward and intuitive, barring a few errors, such as not being able to use apt-get without killing it first. I'm using Ubuntu Karmic because of an admittedly crowdist rationale; if more people are using a system, support should be more established and widespread. 

I've been trying to install kguitar and used apt-get to attempt installation. I get this readout.

edrihan@edrihan-desktop:~$ sudo apt-get install kguitar
[sudo] password for edrihan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kguitar is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 82 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up acroread (9.2-1karmic1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing acroread (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acroread-fonts:
 acroread-fonts depends on acroread (>= 9.1); however:
  Package acroread is not configured yet.
dpkg: error processing acroread-fonts (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 acroread
 acroread-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)


My other problem is slight but noticeable (i.e annoying). I'm using Audacious as a player in Winamp's stead which seems to be reliable enough but I'm finding that sometimes the playback will skip/stop on a single frame.. causing jittery playback. It's good enough to be considered functional but like I said it's very annoying to have a problem not bad enough to be fubar but still annoying. This problem is completely seperate from the aforementioned.

I'm a complete noob to linux and as such no statement of the obvious will be condescending to me. I appreciate anyone helping and will no doubt need to use the services of this community again next time I wallow in confusion at seemingly obtuse errors.

---

