---
title: "Upgrade to Edgy: &quot;Your system could be in an unusable state&quot;"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by McLeod on 2007-01-29
Hello,

I just upgraded from 6.06 LTS to 6.10. During the upgrade I had several problems. Some packages were not installed because of dependencies, and at the end I was told: 

> "The upgrade aborts now. Your system could be in an unusable state. A recovery was run (dpkg --configure -a). installArchives() failed"

I found two prior mentions of this error:
[http://ubuntuforums.org/showthread.php?p=1781805](http://ubuntuforums.org/showthread.php?p=1781805)
[http://forums.mozillazine.org/viewtopic.php?t=479690](http://forums.mozillazine.org/viewtopic.php?t=479690)

But neither answers how to fix the problem. Any ideas? I'm appending the section of my /var/log/dist-upgrade/main.log that contains the errors. I'd be happy to provide any other information.

Thanks!

> 
2007-01-29 10:59:17,078 ERROR got an error from dpkg for pkg: 'python-logilab-astng': 'dependency problems - leaving unconfig
ured
'
2007-01-29 11:00:45,463 DEBUG got a conffile-prompt from dpkg for file: '/etc/cups/cupsd.conf'
2007-01-29 11:05:11,881 ERROR got an error from dpkg for pkg: 'libnautilus-extension1': 'subprocess post-installation script 
killed by signal (Interrupt)
'
2007-01-29 11:05:40,791 ERROR got an error from dpkg for pkg: 'evince': 'dependency problems - leaving unconfigured
'
2007-01-29 11:07:10,685 ERROR got an error from dpkg for pkg: 'file-roller': 'dependency problems - leaving unconfigured
'
2007-01-29 11:08:09,741 ERROR got an error from dpkg for pkg: 'gnome-control-center': 'dependency problems - leaving unconfig
ured
'
2007-01-29 11:08:38,674 ERROR got an error from dpkg for pkg: 'gnome-session': 'dependency problems - leaving unconfigured
'
2007-01-29 11:09:05,104 ERROR got an error from dpkg for pkg: 'gnome-terminal': 'dependency problems - leaving unconfigured
'
2007-01-29 11:09:23,497 ERROR got an error from dpkg for pkg: 'gnome-panel': 'dependency problems - leaving unconfigured
'
2007-01-29 11:15:33,163 WARNING no activity on terminal for 240 seconds (Installed liboobs-1-2)
2007-01-29 11:15:33,380 ERROR got an error from dpkg for pkg: 'gnome-applets': 'dependency problems - leaving unconfigured
'
2007-01-29 11:15:59,234 ERROR got an error from dpkg for pkg: 'gnome-system-tools': 'dependency problems - leaving unconfigur
ed
'
2007-01-29 11:16:13,435 ERROR got an error from dpkg for pkg: 'nautilus': 'dependency problems - leaving unconfigured
'
2007-01-29 11:16:20,179 ERROR got an error from dpkg for pkg: 'nautilus-cd-burner': 'dependency problems - leaving unconfigur
ed
'
2007-01-29 11:16:34,600 ERROR got an error from dpkg for pkg: 'nautilus-sendto': 'dependency problems - leaving unconfigured
'
2007-01-29 11:16:44,933 ERROR got an error from dpkg for pkg: 'totem-gstreamer': 'dependency problems - leaving unconfigured
'
2007-01-29 11:16:58,350 ERROR got an error from dpkg for pkg: 'totem-mozilla': 'dependency problems - leaving unconfigured
'
2007-01-29 11:17:18,139 ERROR got an error from dpkg for pkg: 'ubuntu-desktop': 'dependency problems - leaving unconfigured
'
2007-01-29 11:42:13,789 ERROR SystemError from cache.commit(): installArchives() failed


---

### Post by McLeod on 2007-01-29
Update: I rebooted my system. After logging in, I just get a blank screen with the beige background. I was able to open my terminal with a keyboard command, and can start programs such as Firefox and Nautilus from there, but I have no status bar or menu bar at the top of the screen. Help! I'll give any information necessary.

---

### Post by McLeod on 2007-01-31
Problem fixed! I just went back to synaptic and asked it to reinstall one of the packages that had not been installed properly previously. It automatically reinstalled all the broken packages. I had to restart, but after that, everything worked fine.

---

