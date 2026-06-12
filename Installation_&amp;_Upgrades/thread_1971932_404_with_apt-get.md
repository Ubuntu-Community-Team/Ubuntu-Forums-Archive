---
title: "404 with apt-get"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by Dubslow on 2012-05-03
For the last 2-3 weeks, I've been getting these errors whenever I run "sudo apt-get update":

```
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Err http://us.archive.ubuntu.com precise/main amd64 Packages
  404  Not Found [IP: 91.189.92.182 80]
Err http://us.archive.ubuntu.com precise/universe amd64 Packages
  404  Not Found [IP: 91.189.92.182 80]
Err http://us.archive.ubuntu.com precise/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.182 80]
Err http://us.archive.ubuntu.com precise/main i386 Packages
  404  Not Found [IP: 91.189.92.182 80]
Err http://us.archive.ubuntu.com precise/universe i386 Packages
  404  Not Found [IP: 91.189.92.182 80]
Fetched 6,361 kB in 12min 28s (8,496 B/s)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.182 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.182 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.182 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.182 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.182 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
``` 
Something similar happens when I run "upgrade" some of the files download, but then some don't, and even the ones that did download fine don't get installed because apt-get quits with a relevant error message. (That's one of my complaints about apt-get is that it's terrible at handling errors non-fatally, but of course it would be nice to get the problem fixed.)

I didn't modify my sources.list or anything -- and commenting out some of the lines didn't help. Judging by the errors, it looks like Canonical moved some servers but somehow the DNS didn't get updated. Any thoughts?

---

### Post by newbie-user on 2012-05-03
Try using a different mirror. [http://people.canonical.com/~cjwatson/mirror/list.html](http://people.canonical.com/~cjwatson/mirror/list.html)

---

### Post by Dubslow on 2012-05-03
> **newbie-user said:**
> Try using a different mirror. [http://people.canonical.com/~cjwatson/mirror/list.html](http://people.canonical.com/~cjwatson/mirror/list.html)
Thanks for the tip, but... theory rarely translates to practice :p
```
Err http://ca.archive.ubuntu.com precise/main amd64 Packages                                   
  404  Not Found [IP: 91.189.92.180 80]
Fetched 18.3 MB in 4min 33s (67.0 kB/s)                                                        
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.180 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```
The number of errors went way down, but I still got this one error, which you notice is (almost) the same IP address despite trying to use the Canadian mirror.

---

### Post by TBABill on 2012-05-03
Wondering if you were hitting the servers while they weren't sync'd or traffic was higher than they can handle adequately. Right after releases there are many posts like these with Ubuntu server problems that are resolved within a couple hours.

---

### Post by Dubslow on 2012-05-03
> **TBABill said:**
> Wondering if you were hitting the servers while they weren't sync'd or traffic was higher than they can handle adequately. Right after releases there are many posts like these with Ubuntu server problems that are resolved within a couple hours.
Like I said, it's been like this for a couple of weeks, meaning before 12.04 was officially released; I initially installed the Alpha, and what I'm running now is still likely mostly beta-level programs, because apt-get can't handle errors non-fatally (even though most of the packages do download just fine, it still doesn't install any of them). That is to say, I don't even have the release version because apt-get refuses to upgrade.

Edit: I just tried "update" using the UK mirrors (instead of CA/US) and that worked fine. (It'll take a buttload of time to DL, but better than nothing.)

Edit2: -blam!- it, configuring python2.7 failed and caused a whole mess of errors, and apt-get isn't working properly now and Update Manager segfaults whenever I run it. -blam!- 
Here's what apt-get produces:
```
bill@Durandal:~&#8752;&#8706; sudo apt-get upgrade
Reading package lists... Done
bill@Durandal:~&#8752;&#8706; y tree... 0%
```When I run it, after the Done appears, the prompt appears then the "[dependenc]y tree"  crap appears *after* my cursor. (This happens for every command except "update". python-apt was one of the many packages that failed following python2.7, so now I have no clue what to do.) Edit3: Actually, now apt-get itself is working (no clue why), but the upgrade still fails. I just noticed that python2.7 produces a seg fault (joy!).
```
bill@Durandal:~&#8752;&#8706; sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic usb-creator-common
  usb-creator-gtk
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
28 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python2.7 (2.7.3-0ubuntu3) ...
Segmentation fault
dpkg: error processing python2.7 (--configure):
 subprocess installed post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of python:
 python depends on python2.7 (>= 2.7.3); however:
  Package python2.7 is not configured yet.
dpkg: error processing python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apt:
 python-apt depends on python2.7; however:
  Package python2.7 is not configured yet.
 python-apt depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-apt depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python2.7; however:
  Package python2.7 is not configured yet.
 language-selector-common depeNo apport report written because the error message indicates its a followup error from a previous failure.
                                                        No apport report written because the error message indicates its a followup error from a previous failure.
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                      No apport report written because MaxReports is reached already
                                    No apport report written because MaxReports is reached already
                  No apport report written because MaxReports is reached already
nds on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 language-selector-common depends on python (<< 2.8); however:
  Package python is not configured yet.
 language-selector-common depends on python-apt (>= 0.7.12.0); however:
  Package python-apt is not configured yet.
dpkg: error processing language-selector-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python; however:
  Package python is not configured yet.
 update-notifier-common depends on python-apt (>= 0.6.12); however:
  Package python-apt is not configured yet.
dpkg: error processing update-notifier-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on python; however:
  Package python is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependNo apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                   No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
               No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             ency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gdbm:
 python-gdbm depends on python (>= 2.7); however:
  Package python is not configured yet.
 python-gdbm depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-gdbm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of command-not-found:
 command-not-found depends on python2.7; however:
  Package python2.7 is not configured yet.
 command-not-found depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 command-not-found depends on python (<< 2.8); however:
  Package python is not configured yet.
 command-not-found depends on python-apt; however:
  Package python-apt is not configured yet.
 command-not-found depends on python-gdbm; however:
  Package python-gdbm is not configured yet.
dpkg: error processing command-not-found (--configure):
 dependency proNo apport report written because MaxReports is reached already
                                                                             blems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on language-selector-common; however:
  Package language-selector-common is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python2.7; however:
  Package python2.7 is not configured yet.
 update-manager-core depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 update-manager-core depends on python (<< 2.8); however:
  Package python is not configured yet.
 update-manager-core depends on python-apt (>= 0.7.13.4ubuntu3); however:
  Package python-apt is not configured yet.
dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-problem-report:
 python-problem-report depends on python2.7; however:
  Package python2.7 is not configured yet.
 python-problem-report depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-problem-report depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-problem-report (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python2.7; however:
  Package python2.7 is not configured yet.
 python-apport depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-apport depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-apport depends on python-apt (>= 0.7.9); however:
  Package python-apt is not configured yet.
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python (>= 2.6); however:
  Package python is not configured yet.
 apport depends on python-apport (>= 2.0.1-0ubuntu7); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python (>= 2.4); however:
  Package python is not configured yet.
 apport-gtk depends on python-apport (>= 2.0.1-0ubuntu7); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on update-notifier-common (>= 0.119ubuntu2); however:
  Package update-notifier-common is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on python2.7; however:
  Package python2.7 is not configured yet.
 gedit depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 gedit depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-sudoku:
 gnome-sudoku depends on python2.7; however:
  Package python2.7 is not configured yet.
 gnome-sudoku depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 gnome-sudoku depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing gnome-sudoku (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-gnome:
 language-selector-gnome depends on language-selector-common (= 0.79); however:
  Package language-selector-common is not configured yet.
 language-selector-gnome depends on python2.7; however:
  Package python2.7 is not configured yet.
 language-selector-gnome depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 language-selector-gnome depends on python (<< 2.8); however:
  Package python is not configured yet.
 language-selector-gnome depends on python-apt (>= 0.6.12); however:
  Package python-apt is not configured yet.
dpkg: error processing language-selector-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython2.7:
 libpython2.7 depends on python2.7 (= 2.7.3-0ubuntu3); however:
  Package python2.7 is not configured yet.
dpkg: error processing libpython2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-central:
 python-central depends on python (>= 2.4.3-10); however:
  Package python is not configured yet.
dpkg: error processing python-central (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gobject-2:
 python-gobject-2 depends on python2.7; however:
  Package python2.7 is not configured yet.
 python-gobject-2 depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-gobject-2 depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-gobject-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-common:
 unity-common depends on python; however:
  Package python is not configured yet.
dpkg: error processing unity-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on unity-common (= 5.10.0-0ubuntu6); however:
  Package unity-common is not configured yet.
 unity depends on python; however:
  Package python is not configured yet.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python2.7; however:
  Package python2.7 is not configured yet.
 update-manager depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 update-manager depends on python (<< 2.8); however:
  Package python is not configured yet.
 update-manager depends on update-manager-core (= 1:0.156.14.1); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 0.119ubuntu8.1); however:
  Package update-notifier-common is not configured yet.
 update-notifier depends on python; however:
  Package python is not configured yet.
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xdiagnose:
 xdiagnose depends on python2.7; however:
  Package python2.7 is not configured yet.
 xdiagnose depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 xdiagnose depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing xdiagnose (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gedit; however:
  Package gedit is not configured yet.
 ubuntu-desktop depends on language-selector-gnome; however:
  Package language-selector-gnome is not configured yet.
 ubuntu-desktop depends on unity; however:
  Package unity is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
 ubuntu-desktop depends on xdiagnose; however:
  Package xdiagnose is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sessioninstaller:
 sessioninstaller depends on python2.7; however:
  Package python2.7 is not configured yet.
 sessioninstaller depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 sessioninstaller depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing sessioninstaller (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 python2.7
 python
 python-apt
 language-selector-common
 update-notifier-common
 ubuntu-minimal
 python-gdbm
 command-not-found
 ubuntu-standard
 update-manager-core
 python-problem-report
 python-apport
 apport
 apport-gtk
 flashplugin-installer
 gedit
 gnome-sudoku
 language-selector-gnome
 libpython2.7
 python-central
 python-gobject-2
 unity-common
 unity
 update-manager
 update-notifier
 xdiagnose
 ubuntu-desktop
 sessioninstaller
E: Sub-process /usr/bin/dpkg returned an error code (1)
bill@Durandal:~&#8752;&#8706; 
```Some of those packages look big enough that I'm scared to shut it down.

---

