---
title: "sudo apt, dpkg and mariadb problems"
date: 2020-04-27
forum: Installation &amp; Upgrades
---

### Post by pegasusp on 2020-04-27
when i run `sudo apt upgrade`
```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
when i run `[COLOR=#2D3748][FONT=&quot]sudo systemctl status mariadb`
[/FONT][/COLOR]```

&#9679; mariadb.service - MariaDB 10.1.44 database server
   Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset:
   Active: activating (start) since Mon 2020-04-27 22:49:23 EEST; 9min ago
     Docs: man:mysqld(8)
           https://mariadb.com/kb/en/library/systemd/
  Process: 8112 ExecStartPre=/bin/sh -c [ ! -e /usr/bin/galera_recovery ] && VAR
  Process: 8110 ExecStartPre=/bin/sh -c systemctl unset-environment _WSREP_START
  Process: 8109 ExecStartPre=/usr/bin/install -m 755 -o mysql -g root -d /var/ru
 Main PID: 8247 (mysqld)
    Tasks: 26 (limit: 2359)
   CGroup: /system.slice/mariadb.service
           &#9492;&#9472;8247 /usr/sbin/mysqld


Apr 27 22:49:23 itsavps systemd[1]: Starting MariaDB 10.1.44 data
Apr 27 22:49:23 itsavps mysqld[8247]: 2020-04-27 22:49:23 1397296
lines 1-15/15 (END)

```

when i run [COLOR=#000000][FONT=&quot]sudo apt-get -f install
[/FONT][/COLOR]```
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
when i run `sudo dpkg --configure -a`
```
dpkg: error: dpkg status database is locked by another process
```


My Current sources.list : 
```

#deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://in.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ bionic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ bionic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ bionic universe
deb http://in.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://in.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner


deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe

# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

Please i need quick help i am trying to install MariaDB i recently tried to upgrade to 18.04 LTS

---

### Post by QIII on 2020-04-27
The messages indicate that some other process is trying to install software.  Only one process at a time can do that.

Do you have you system set up to do automatic updates?  Are you running install from more than one terminal?  Do you have Synaptic or the Software Centre open?

---

### Post by pegasusp on 2020-04-27
No. I am using Linux VPS

---

### Post by pegasusp on 2020-04-27
I'll be really happy if someone help me to fix all errors step by step with terminal :)

---

### Post by QIII on 2020-04-27
It really doesn't matter that it is a VPS.  Only one process can use package management at a time no matter what machine the OS is installed on. 

The message you are getting is a clear indication that your are attempting to update or install when another process is already doing that.

Please first be sure that is not the case, then we can try something else.

---

### Post by pegasusp on 2020-04-27
Yeah i am sure that is the case. dpkg have locked some files such as config.dat,[COLOR=#000000][FONT=&amp]lock,[/FONT][/COLOR][COLOR=#000000][FONT=&amp]lock-freunted,passwords.dat,templates.dat
[/FONT][/COLOR]_**I tried "sudo rm" "sudo lsof" nothing really worked, I really need to fix this problem ASAP.**_

---

### Post by QIII on 2020-04-27
There are methods that involve removing one of a couple of files.  That method, however, is dangerous in my opinion.

You might try rebooting the machine.  Are you administering in over SSH or via a control panel of some sort?

---

### Post by pegasusp on 2020-04-27
[IMG]https://prnt.sc/s7432p[/IMG]I am removing lock and lock-frontend with "sudo rm" and they keep coming back. also [check this photo]("https://prnt.sc/s7432p")

---

### Post by QIII on 2020-04-28
Lock-frontend means that a GUI package manager is running.  Is this a server install or a desktop install?

---

