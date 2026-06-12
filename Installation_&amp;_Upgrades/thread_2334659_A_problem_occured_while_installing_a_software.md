---
title: "A problem occured while installing a software"
date: 2016-08-21
forum: Installation &amp; Upgrades
---

### Post by marcandy on 2016-08-21
[COLOR=#111111][FONT=Ubuntu]I'm having trouble installing updates on my Ubuntu 16.04 Every time there is a software update and I try to do the install. It worked for a while then it says "operation failed" etc... I don't know what is the cause, I would like some help troubleshooting the issue. This the error in the terminal when I do: sudo apt-get update && sudo apt-get upgrade

[/FONT][/COLOR]```
tart: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
dpkg: error processing package runit (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of git-daemon-run:
 git-daemon-run depends on runit; however:
  Package runit is not configured yet.


dpkg: error processing package git-daemon-run (--configure):
 dependency problems - leaving unconfigured
Setting up compiz-core (1:0.9.12.2+16.04.20160801.3-0ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up libcompizconfig0:amd64 (1:0.9.12.2+16.04.20160801.3-0ubuntu1) ...
Setting up libdecoration0:amd64 (1:0.9.12.2+16.04.20160801.3-0ubuntu1) ...
Setting up compiz-plugins-default:amd64 (1:0.9.12.2+16.04.20160801.3-0ubuntu1) ...
Setting up compiz-gnome (1:0.9.12.2+16.04.20160801.3-0ubuntu1) ...
Setting up compiz (1:0.9.12.2+16.04.20160801.3-0ubuntu1) ...
Setting up python3-software-properties (0.96.20.4) ...
Setting up software-properties-common (0.96.20.4) ...
Setting up software-properties-gtk (0.96.20.4) ...
Setting up python-compizconfig:amd64 (1:0.9.12.2+16.04.20160801.3-0ubuntu1) ...
Setting up compizconfig-settings-manager (1:0.9.12.2+16.04.20160801.3-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 runit
 git-daemon-run
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

Reading package lists... Done
Building dependency tree 
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up runit (2.1.2-3ubuntu1) ...
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
dpkg: error processing package runit (--configure):
subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of git-daemon-run:
git-daemon-run depends on runit; however:
Package runit is not configured yet.


dpkg: error processing package git-daemon-run (--configure):
dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
runit
git-daemon-run
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by T.J. on 2016-08-21
Have you tried: 
sudo apt-get update
sudo apt-get install -f  (to finish installing packages)

or 

sudo apt-get update
sudo dpkg --configure -a  (to fix broken configurations)


 If you still have trouble after that, post back to me and I'll try to help you.  It's possible if you are using a third party PPA, that a bad package has broken your install.  It's also possible that the package manager was simply interrupted, and just needs to finish.  Running those commands may tell us which it is.

---

### Post by marcandy on 2016-08-21
I think I fixed it. I'm able to do sudo apt-get update now. I used this to fix it: [http://askubuntu.com/questions/765565/how-to-fix-processing-with-runit-and-git-daemon-run](http://askubuntu.com/questions/765565/how-to-fix-processing-with-runit-and-git-daemon-run)

```
[COLOR=#111111][FONT=Ubuntu]sudo apt-get purge runit[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo apt-get purge git-all[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo apt-get purge git[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo apt-get autoremove[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo apt update[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo apt install git[/FONT][/COLOR]
```

and this to remove crashes [http://askubuntu.com/questions/365358/im-getting-a-lot-of-system-program-problem-detected-error-dialogs-is-there-a](http://askubuntu.com/questions/365358/im-getting-a-lot-of-system-program-problem-detected-error-dialogs-is-there-a)
```

sudo rm /var/crash/*
```

Thanks anyway.

---

