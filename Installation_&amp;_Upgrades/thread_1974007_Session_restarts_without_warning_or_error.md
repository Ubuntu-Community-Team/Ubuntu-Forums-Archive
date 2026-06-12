---
title: "Session restarts without warning or error"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by Xelort on 2012-05-05
Hi.
After upgrading from 10.04 to 12.04 on my desktop machine, i have an unstability issue.

Sometimes, couldn't figured out yet when or why exactly, in a blink of an eye there's the login screen again. No warnings, no error messages, no nothing: just the login screen. 

When that happens, all my applications are closed by force: i can't find my losts programs running anywhere, not even with "ps".

I **GUESS** (not sure really) it **MAY** have something to do with sound. That's because two times it happened i was playing music with VLC media player. My girlfriend tells me it also happened to her, but while using Banshee. 
However, everytime it happens, i'm using many applications (like firefox, apt-get, and so on).

Don't know where to check for a clue about this. 
It's serious. **I lost all my work everytime it happens**, without chance of saving it. About an hour ago lost something like 600MB that Synaptic was downloading (while installing debian science packages).
Right now i'm working on home and i fear to play music on my computer because it could crash. :(
This never happened on 10.04.

Any idea?
Thanks.

---

### Post by dino99 on 2012-05-05
several things to check:

- is the graphic driver activated ? (sudo jockey-gtk)
- check the sources.list to be sure only using genuine Precise packages; if not, then open synaptic to downgrade these packages (file -> force version menu) or use ppa-purge if you are using some.

- clean the system with bleachbit (as root)
- reboot
then run:
sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

note: your best trouble friends are the logs (/var/log/ & .xsession-errors inside /home, ctrl+h to unhide it)

---

### Post by Xelort on 2012-05-05
It happened again a minute ago :(
And this time i was just scrolling while reading a web page; no sound app involved.

There was also Synaptic, again, downloading, again, debian science metapackages (1.6 GB total selection).

So... now i fear using Synaptic. :(

---

### Post by Xelort on 2012-05-05
> **dino99 said:**
> several things to check:

- is the graphic driver activated ? (sudo jockey-gtk)
- check the sources.list to be sure only using genuine Precise packages; if not, then open synaptic to downgrade these packages (file -> force version menu) or use ppa-purge if you are using some.

- clean the system with bleachbit (as root)
- reboot
then run:
sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

note: your best trouble friends are the logs (/var/log/ & .xsession-errors inside /home, ctrl+h to unhide it)

Thanks! 
Didn't saw this answer before. I'll go check this out right now.

---

### Post by dino99 on 2012-05-05
> **Xelort said:**
> It happened again a minute ago :(
And this time i was just scrolling while reading a web page; no sound app involved.

There was also Synaptic, again, downloading, again, debian science metapackages (1.6 GB total selection).

So... now i fear using Synaptic. :(

are you having some micro power instability ? i mean electric main power installation, or getting some electric storm.

---

### Post by Xelort on 2012-05-05
Well, dpkg-reconfigure is still working, but i can give you some data in the meantime:

> 
- is the graphic driver activated ? (sudo jockey-gtk)
Yes. I'm using compiz effects (like desktop cobe and wobly windows).
Weeks or months before updating i was using a driver from nvidia website. That's because Ubuntu's driver wasn't compatible with WebGL (i'm a developer); had to update my drivers.

However, i had no issue before upgrading to 12.04.

> 
- check the sources.list to be sure only using genuine Precise packages;  if not, then open synaptic to downgrade these packages (file ->  force version menu) or use ppa-purge if you are using some.
Don't know what "genuine precise packages" means. I have enabled all the packages the distro upgrade put there, and some others i usually have manually added: like Firefox's PPA, kicad, gimp, or wine. 
This is my /etc/apt/sources.list

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
# deb http://wine.budgetdedicated.com/apt karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic
# deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu precise main # disabled on upgrade to precise
# deb ftp://savonet.rastageeks.org/ ./
# deb http://www.debian-multimedia.org lenny main
# deb http://backports.debian.org/debian-backports lenny-backports main
# deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu precise main # disabled on upgrade to precise
deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu precise-backports restricted main multiverse universe

```> 
- clean the system with bleachbit (as root)
Did it. Installed and cleaned.

> 
sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
I did "sudo apt-get clean && sudo apt-get update". Then "sudo apt-get install -f". And then " sudo dpkg-reconfigure -phigh -a". 

dpkg-reconfigure finished now. Here's the output:

```

Xelort@Desktop:~$ sudo dpkg-reconfigure -phigh -a
Package `wine1.4-i386' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: wine1.4-i386 is not installed
Xelort@Desktop:~$ 

```> 
note: your best trouble friends are the logs (/var/log/ & .xsession-errors inside /home, ctrl+h to unhide it)
I've found this in /var/log/auth.log :


```

May  5 14:00:36 Desktop polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session4 (system bus name :1.110, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
May  5 14:00:36 Desktop lightdm: pam_unix(lightdm:session): session closed for user Xelort
May  5 14:00:37 Desktop sudo: pam_unix(sudo:session): session closed for user root
May  5 14:00:37 Desktop lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
May  5 14:00:37 Desktop lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :2
May  5 14:00:38 Desktop lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "Xelort"
May  5 14:00:38 Desktop dbus[1130]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.147" (uid=136 pid=28843 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1850 comm="/usr/sbin/console-kit-daemon --no-daemon ")
May  5 14:00:40 Desktop dbus[1130]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.155" (uid=136 pid=28883 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1850 comm="/usr/sbin/console-kit-daemon --no-daemon ")
May  5 14:02:03 Desktop lightdm: pam_unix(lightdm:session): session closed for user lightdm
May  5 14:02:03 Desktop lightdm: pam_unix(lightdm:session): session opened for user Xelort by (uid=0)
May  5 14:02:03 Desktop lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :2
May  5 14:02:04 Desktop polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session6 (system bus name :1.161 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May  5 14:02:06 Desktop dbus[1130]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.173" (uid=1000 pid=29450 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1850 comm="/usr/sbin/console-kit-daemon --no-daemon ")
May  5 14:05:01 Desktop CRON[30581]: pam_unix(cron:session): session opened for user root by (uid=0)
May  5 14:05:01 Desktop CRON[30581]: pam_unix(cron:session): session closed for user root
May  5 14:09:01 Desktop CRON[31761]: pam_unix(cron:session): session opened for user root by (uid=0)
May  5 14:09:01 Desktop CRON[31761]: pam_unix(cron:session): session closed for user root
May  5 14:10:01 Desktop CRON[32129]: pam_unix(cron:session): session opened for user root by (uid=0)
May  5 14:10:01 Desktop CRON[32129]: pam_unix(cron:session): session closed for user root
May  5 14:12:31 Desktop sudo: Xelort : TTY=pts/0 ; PWD=/home/Xelort ; USER=root ; COMMAND=/usr/bin/apt-get install bleachbit

```I guess that shows the activity between the forced logout and the bleachbit installation (inmediatelly after reading about it in this thread).

The other logs didn't seemed to show any relevant data. [I]
.xsession-errors [/I]doesn't have timestamp =/
Oh... and BTW... i guess bleachbit deleted it >_<
It's not there anymore.


> 
are you having some micro power instability ? i mean electric main power installation, or getting some electric storm.     
Micro is fine, video and memory are fine, it all begun after 12.04. 10.04 worked like a charm. I can run tests to check that out, but i find it pointless without a serious clue about this not being a software problem.

Thanks.

---

### Post by Xelort on 2012-05-05
Update.

It happened again. And it was using VLC Media Player at the same time that Synaptic once again.

So, i went to check logs, and found this on */var/log/apport.log*:

```

ERROR: apport (pid 11311) Sat May  5 13:12:06 2012: called for pid 1484, signal 11
ERROR: apport (pid 11311) Sat May  5 13:12:06 2012: Unhandled exception:
Traceback (most recent call last):
  File "/usr/share/apport/apport", line 282, in <module>
    info.add_proc_info(pid)
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 431, in add_proc_info
    raise ValueError('invalid process')
ValueError: invalid process
ERROR: apport (pid 11311) Sat May  5 13:12:06 2012: pid: 11311, uid: 0, gid: 0, euid: 0, egid: 0
ERROR: apport (pid 11311) Sat May  5 13:12:06 2012: environment: {}
ERROR: apport (pid 28739) Sat May  5 14:00:36 2012: called for pid 11324, signal 11
ERROR: apport (pid 28739) Sat May  5 14:00:36 2012: Unhandled exception:
Traceback (most recent call last):
  File "/usr/share/apport/apport", line 282, in <module>
    info.add_proc_info(pid)
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 431, in add_proc_info
    raise ValueError('invalid process')
ValueError: invalid process
ERROR: apport (pid 28739) Sat May  5 14:00:36 2012: pid: 28739, uid: 0, gid: 0, euid: 0, egid: 0
ERROR: apport (pid 28739) Sat May  5 14:00:36 2012: environment: {}
ERROR: apport (pid 6568) Sat May  5 19:22:31 2012: called for pid 1453, signal 11
ERROR: apport (pid 6568) Sat May  5 19:22:31 2012: Unhandled exception:
Traceback (most recent call last):
  File "/usr/share/apport/apport", line 282, in <module>
    info.add_proc_info(pid)
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 431, in add_proc_info
    raise ValueError('invalid process')
ValueError: invalid process
ERROR: apport (pid 6568) Sat May  5 19:22:31 2012: pid: 6568, uid: 0, gid: 0, euid: 0, egid: 0
ERROR: apport (pid 6568) Sat May  5 19:22:31 2012: environment: {}

```

Three apport unhandled exceptions, and every single one of them exactly at the time my system crashed.
So, i guess it's apport failing to show the error what is crashing my session.

.xsession-errors is back, but it doesn't have any timestamp in the log lines, so i can't tell about matching problems.


What can i do with this apport thing?

---

### Post by Xelort on 2012-05-05
I've reported a bug stating all this in launchpad's apport section.
Here's the link: [https://bugs.launchpad.net/apport/+bug/995294](https://bugs.launchpad.net/apport/+bug/995294)

---

### Post by joe carolan on 2012-05-08
same problem (solved by installing GDM see link below

[http://askubuntu.com/questions/130387/stuck-at-login-screen](http://askubuntu.com/questions/130387/stuck-at-login-screen)

---

