---
title: "Virtual Machine Upgrade of 14.04 to 16.04 fails"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by nadpro on 2016-09-23
I have multiple 14.04 VM's that I have been running since 14.04 came out  they are all up to date to 14.04.5 but I would like to upgrade them to 16.04.1.  I have tried several times and with 2 different VM hosts with no luck.  It always gets stuck at asking permission to restart services without asking.  It overlays a root@server# and does not continue the upgrade.  after performing a reboot I get a long list of broken packages and the OS after that point is completely worthless.  Luckily I keep backups of all my VHD's so it is an easy restore but I really don't want to rebuild all of my VM's from scratch so I can be on 16.04.  I have tried running them in both VMWare workstation 12 pro and Virtualbox.

Unfortunately the way things are going I may have to rebuild everything anyway because I am trying to switch over to ESXi and it does not like VMWare Workstation pro at all.  No compatibility between its own products?  What is going on VMWare?  Since when did you become Microsoft?

At any rate, any insight would be appreciated.

---

### Post by ian-weisser on 2016-09-23
> **nadpro said:**
> It always gets stuck at asking permission to restart services without asking. It overlays a root@server# and does not continue the upgrade. after performing a reboot I get a long list of broken packages and the OS after that point is completely worthless. 

Please pull the relevant bits from /var/log/dist-upgrade and show us as much detail asyou can.

Release-upgrades are extensively tested...but not with non-Ubuntu (therefore unsupported) software.
Generally, best practice before upgrading is to uninstall all non-Ubuntu software. Return the system to as close to stock install as possible. Then do the release-upgrade. Then re-install all your non-Ubuntu software.

---

### Post by nadpro on 2016-09-23
To be honest I am not sure what would be relevant or which of the logs to pull from.  As for the machine itself it was only a appache web server with php, the other server I tried was just a FTP server, absolutely nothing special but locked up at the exact same spot.  Looking in the /var/log/dist-upgrade directory I see apt.log history.log main.log apt-term.log lspci.txt and screenlog.0  ther is also a apt-clone_system_state.tar.gz and folder labled 20160922-2039 with a min.log in it.  Which one should I be looking in and what information would be most useful?  Thank you for you help.

---

### Post by ian-weisser on 2016-09-24
When you examine the log files, you will figure out pretty quickly the parts we care about:
The error messages.
The session leading up to the error messages.
How the system recovered from the error messages.

Er, please don't give us your entire /var/log/dist-upgrade/apt-term.log and apt.log. Please edit lightly down to the relevant sessions.

---

### Post by nadpro on 2016-09-24
ok, so I am happy and at the same time confused and upset.  I had restored my old images so my servers would be working and had to attempt to upgrade them again in order to get the error logs.  I have been trying to do upgrades since 16.04.1 was released and have been having this issue ever since.  This morning I performed the upgrade the same way I have been at least 30 times by now, all with the same failure.  Today they somehow for some reason worked without issue.  I am happy they now work but don't like not knowing why.  Yesterday was the first time I had asked for help on this issue so something here seems a little to coincidental.  perhaps this has been a known issue and they patched it last night?  But I have been searching the forums and found no one with the issue I have been having.  Again I am glad it worked but am confused as to why.

Thank you for your help, or at least trying.

---

