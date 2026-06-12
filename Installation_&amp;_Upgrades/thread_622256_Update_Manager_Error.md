---
title: "Update Manager Error"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by spenc083 on 2007-11-24
Tried killing apt-get process but the process is not running:
=====
The following error is not allowing me to run updates:
=====

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 48 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Thanks,

---

### Post by spenc083 on 2007-11-24
Sorry, I forgot the following results:
================
keithb@ubuntuspenc0:~$ sudo aptitude update
Password:
E: Type 'sudo' is not known on line 48 in source list /etc/apt/sources.list
E: Couldn't read list of package sources
keithb@ubuntuspenc0:~$ ps -a
  PID TTY          TIME CMD
 5836 pts/0    00:00:00 ps
keithb@ubuntuspenc0:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
   30 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kacpid
   32 ?        00:00:00 kacpi_notify
   98 ?        00:00:00 kseriod
  117 ?        00:00:00 pdflush
  118 ?        00:00:00 pdflush
  119 ?        00:00:00 kswapd0
  120 ?        00:00:00 aio/0
 1948 ?        00:00:00 ata/0
 1949 ?        00:00:00 ata_aux
 1954 ?        00:00:00 ksuspend_usbd
 1955 ?        00:00:00 khubd
 2296 ?        00:00:00 kjournald
 2495 ?        00:00:00 udevd
 3354 ?        00:00:00 kpsmoused
 3521 ?        00:00:00 kgameportd
 4005 tty4     00:00:00 getty
 4006 tty5     00:00:00 getty
 4010 tty2     00:00:00 getty
 4011 tty3     00:00:00 getty
 4012 tty1     00:00:00 getty
 4013 tty6     00:00:00 getty
 4251 ?        00:00:00 acpid
 4357 ?        00:00:00 syslogd
 4413 ?        00:00:00 dd
 4415 ?        00:00:00 klogd
 4436 ?        00:00:00 dbus-daemon
 4452 ?        00:00:05 hald
 4453 ?        00:00:00 hald-runner
 4459 ?        00:00:00 hald-addon-acpi
 4467 ?        00:00:00 hald-addon-keyb
 4476 ?        00:00:00 hald-addon-keyb
 4479 ?        00:00:00 hald-addon-keyb
 4491 ?        00:00:00 hald-addon-stor
 4493 ?        00:00:00 hald-addon-stor
 4506 ?        00:00:00 dhcdbd
 4521 ?        00:00:00 NetworkManager
 4538 ?        00:00:00 avahi-daemon
 4539 ?        00:00:00 avahi-daemon
 4552 ?        00:00:00 NetworkManagerD
 4566 ?        00:00:00 system-tools-ba
 4567 ?        00:00:00 dbus-daemon
 4605 ?        00:00:00 gdm
 4613 ?        00:00:00 gdm
 4630 tty7     00:01:11 Xorg
 4676 ?        00:00:00 dhclient
 4724 ?        00:00:00 hpiod
 4744 ?        00:00:00 python
 4856 ?        00:00:00 hcid
 4878 ?        00:00:00 krfcommd
 4927 ?        00:00:00 atd
 4941 ?        00:00:00 cron
 5043 ?        00:00:00 x-session-manag
 5081 ?        00:00:00 ssh-agent
 5084 ?        00:00:00 dbus-launch
 5085 ?        00:00:00 dbus-daemon
 5087 ?        00:00:01 gconfd-2
 5090 ?        00:00:00 gnome-keyring-d
 5092 ?        00:00:00 gnome-settings-
 5099 ?        00:00:00 sh
 5100 ?        00:00:00 esd
 5105 ?        00:00:00 bonobo-activati
 5110 ?        00:00:01 vino-server
 5111 ?        00:00:02 metacity
 5114 ?        00:00:05 gnome-panel
 5115 ?        00:00:03 nautilus
 5126 ?        00:00:00 gnome-vfs-daemo
 5130 ?        00:00:00 trashapplet
 5131 ?        00:00:00 gnome-volume-ma
 5148 ?        00:00:00 mixer_applet2
 5150 ?        00:00:00 update-notifier
 5152 ?        00:00:00 evolution-alarm
 5154 ?        00:00:00 mapping-daemon
 5156 ?        00:00:00 nm-applet
 5157 ?        00:00:00 gnome-cups-icon
 5159 ?        00:00:00 gnome-power-man
 5180 ?        00:00:00 evolution-data-
 5234 ?        00:00:02 gnome-screensav
 5255 ?        00:06:46 firefox-bin
 5374 ?        00:00:00 cupsd
 5412 ?        00:00:01 gedit
 5794 ?        00:00:00 gnome-terminal
 5796 ?        00:00:00 gnome-pty-helpe
 5797 pts/0    00:00:00 bash
 5841 pts/0    00:00:00 ps
keithb@ubuntuspenc0:~$ sudo killall apt-get
apt-get: no process killed

---

### Post by rsambuca on 2007-11-24
Your repositories are messed up.  Post the output of 

cat /etc/apt/sources.list

---

### Post by spenc083 on 2007-11-25
R, thanks for the quick response. Now from doing my own research tell me if I'm wrong. The version I'm currently running 7.04 is not supported? I had a similar problem on my Latitude laptop but the upgrade to 7.10 crashed the system. I ended up reinstalling on the Latitude.

=======
keithb@ubuntuspenc0:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
sudo apt-get update

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
keithb@ubuntuspenc0:~$

---

### Post by rsambuca on 2007-11-25
> **spenc083 said:**
> R, thanks for the quick response. Now from doing my own research tell me if I'm wrong. The version I'm currently running 7.04 is not supported? I had a similar problem on my Latitude laptop but the upgrade to 7.10 crashed the system. I ended up reinstalling on the Latitude.

=======
keithb@ubuntuspenc0:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
**[COLOR="Red"]sudo apt-get update[/COLOR]**

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
keithb@ubuntuspenc0:~$
You need to open the file in a text editor and delete the line I highlighted in red.  To do this, enter ```
gksudo gedit /etc/apt/sources.list
```Delete the line, save the file and then try an update and upgrade.

---

