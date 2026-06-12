---
title: "[SOLVED] MythTV Upgrade Fails"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by telseth on 2008-09-26
Yesterday I ran apt-get upgrade and it showed new mythtv packages (0.21.0+fixes18379-0ubuntu1) so I hit Y like normal.  dpkg is having a hard time configuring mythtv-common so it has failed.  I tried removing mythtv and reinstalling, but that has left me with no mythtv.

**Here is the output of apt-get install mythtv:**

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up mythtv-common (0.21.0+fixes18379-0ubuntu1) ...
dpkg: error processing mythtv-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv-database:
 mythtv-database depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-database (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-transcode-utils:
 mythtv-transcode-utils depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-transcode-utils (--configure):
 dependency problems - leNo apport report written because the error message indicates its a followup error from a previous failure.
                                                   No apport report written because the error message indicates its a followup error from a previous failure.
                                                                             No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already
                       aving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
 mythtv-backend depends on mythtv-transcode-utils (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-transcode-utils is not configured yet.
dpkg: error processing mythtv-backend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-database is not configured yet.
 mythtv depends on mythtv-frontend (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-frontend is not configured yet.
 mythtv depends on mythtv-backend (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-common
 mythtv-database
 mythtv-frontend
 mythtv-transcode-utils
 mythtv-backend
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)

**Here is what happens when I try to do sudo dpkg --configure mythtv-common:**

Setting up mythtv-common (0.21.0+fixes18379-0ubuntu1) ...
dpkg: error processing mythtv-common (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-common

**Here is sudo aptitude why mythtv-common:**

u   mythtv          Depends mythtv-frontend (= 0.21.0+fixes18379-0ubuntu1)
u A mythtv-frontend Depends mythtv-common (= 0.21.0+fixes18379-0ubuntu1)

I am at a loss, this had never happened before.  Yes, I am running Intrepid, but it was the only system that was able to use my cdrom drive during install.  It has been running great for a month now... until yesterday.

Any other advice would be greatly appreciated.  I miss my tv.

---

### Post by wolfen69 on 2008-09-26
try
```
sudo dpkg --configure -a
```
and
```
sudo apt-get install -f
```
also consider installing [Mythbuntu 8.10]("http://mythbuntu.org/download/?file=mythbuntu-8.10-alpha6-desktop-i386.iso"). having myth tv preinstalled seemed to work better for me. if you like gnome, just install ubuntu-desktop after you install.

---

### Post by telseth on 2008-09-26
**sudo dpkg --configure -a**
Setting up mythtv-common (0.21.0+fixes18379-0ubuntu1) ...
dpkg: error processing mythtv-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv-transcode-utils:
 mythtv-transcode-utils depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-transcode-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
 mythtv-backend depends on mythtv-transcode-utils (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-transcode-utils is not configured yet.
dpkg: error processing mythtv-backend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-database:
 mythtv-database depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-database (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-database is not configured yet.
 mythtv depends on mythtv-frontend (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-frontend is not configured yet.
 mythtv depends on mythtv-backend (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-common
 mythtv-transcode-utils
 mythtv-backend
 mythtv-frontend
 mythtv-database
 mythtv

**sudo apt-get install -f**
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mythtv-common (0.21.0+fixes18379-0ubuntu1) ...
dpkg: error processing mythtv-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv-database:
 mythtv-database depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-database (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-transcode-utils:
 mythtv-transcode-utils depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-transcode-utils (--configure):
 dependency problems - leNo apport report written because the error message indicates its a followup error from a previous failure.
                                                   No apport report written because the error message indicates its a followup error from a previous failure.
                                                                             No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already
                       aving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on mythtv-common (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-common is not configured yet.
 mythtv-backend depends on mythtv-transcode-utils (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-transcode-utils is not configured yet.
dpkg: error processing mythtv-backend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-database is not configured yet.
 mythtv depends on mythtv-frontend (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-frontend is not configured yet.
 mythtv depends on mythtv-backend (= 0.21.0+fixes18379-0ubuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-common
 mythtv-database
 mythtv-frontend
 mythtv-transcode-utils
 mythtv-backend
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)

I really don't want to reinstall, after re-setting up all my users / websites / etc. it's more than a day of work.  Am I stuck until they release the next package version?

---

### Post by telseth on 2008-09-26
Figured out my issue.  My mythtv user was messed up, I changed the uid on it to 1001 so that I can have it auto-log in and start mythtv.  I think I'll create yet another user for that purpose.

To fix:

sudo cp -R /home/mythtv /home/mythtv-backup
sudo userdel -r mythtv
sudo apt-get install -f

A day of pain over... :)

---

### Post by gsanse on 2008-12-01
I was having exactly the same problem, this post saved me,thank you very much!!

---

### Post by T.B. on 2009-03-17
> **telseth said:**
> To fix:

sudo cp -R /home/mythtv /home/mythtv-backup
sudo userdel -r mythtv
sudo apt-get install -f

This ultimately worked for me, but there was an additional problem to be overcome:  userdel would fail with this error:
[INDENT][FONT="Courier New"]userdel: user mythtv is currently logged in[/FONT][/INDENT]

I tried killing all of mythtv's running processes.  There was always one remaining process owned by mythtv, "-sh" which I assume is due to the autologin.  I tried disabling autologin in /etc/gdm/gdm.conf-custom and rebooting, but this process was still around.

I tried "sudo telinit 3" which finally got rid of this remaining mythtv process.  "sudo userdel -r mythtv" *still* complained!  

I did a "who /var/run/utmp" which showed a number of processes which, if I understand utmp correctly, *had* been run at some point my mythtv.  As I understand, this is what userdel is interpreting.  I finally resorted to "sudo cat /dev/null > /var/run/utmp".  I was finally able to run "userdel" and perform the apt-get installation!

Sorry about the verbosity, but I'm not enough of a Linux expert to understand the full implications of each step.  One or more of them may have been the solution.  If I were doing it over, I would probably try this whole sequence:
[INDENT][FONT="Courier New"][B]sudo cp -R /home/mythtv /home/mythtv-backup
sudo telinit 3
sudo cat /dev/null > /var/run/utmp
sudo userdel -r mythtv
sudo apt-get install -f[/B][/FONT][/INDENT]

---

