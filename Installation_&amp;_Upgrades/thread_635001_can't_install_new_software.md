---
title: "can't install new software"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by tOaDeR2005 on 2007-12-08
every time I try to install new software (like mp3 support), I get this message:Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). It does this even after a reboot. I am not using it for anything else. i even quit adept_updater from the system tray.

i'm using Kubuntu 7.10

---

### Post by taurus on 2007-12-08
Open a terminal and post the output of this command here.

```
ps -A
```

---

### Post by tOaDeR2005 on 2007-12-08
here it is:

```
PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   26 ?        00:00:00 kblockd/0
   27 ?        00:00:00 kacpid
   28 ?        00:00:00 kacpi_notify
   90 ?        00:00:00 kseriod
  111 ?        00:00:00 pdflush
  112 ?        00:00:00 pdflush
  113 ?        00:00:00 kswapd0
  165 ?        00:00:00 aio/0
 1963 ?        00:00:00 ksuspend_usbd
 1964 ?        00:00:00 khubd
 2138 ?        00:00:00 ata/0
 2139 ?        00:00:00 ata_aux
 2391 ?        00:00:00 scsi_eh_0
 2392 ?        00:00:00 usb-storage
 2452 ?        00:00:00 kjournald
 2657 ?        00:00:00 udevd
 3550 ?        00:00:00 kpsmoused
 3615 ?        00:00:00 kgameportd
 3893 ?        00:00:01 mount.ntfs
 3894 ?        00:00:00 kjournald
 3895 ?        00:00:00 kjournald
 4135 tty4     00:00:00 getty
 4136 tty5     00:00:00 getty
 4138 tty2     00:00:00 getty
 4146 tty3     00:00:00 getty
 4149 tty1     00:00:00 getty
 4150 tty6     00:00:00 getty
 4321 ?        00:00:00 acpid
 4358 ?        00:00:00 kondemand/0
 4431 ?        00:00:00 syslogd
 4487 ?        00:00:00 dd
 4489 ?        00:00:00 klogd
 4510 ?        00:00:01 dbus-daemon
 4526 ?        00:00:00 NetworkManager
 4540 ?        00:00:00 NetworkManagerD
 4559 ?        00:00:01 hald
 4560 ?        00:00:00 hald-runner
 4601 ?        00:00:00 hald-addon-keyb
 4605 ?        00:00:00 hald-addon-keyb
 4606 ?        00:00:00 hald-addon-keyb
 4607 ?        00:00:00 hald-addon-keyb
 4611 ?        00:00:00 hald-addon-acpi
 4652 ?        00:00:00 kdm
 4665 tty7     00:07:54 Xorg
 4681 ?        00:00:00 kdm
 4683 ?        00:00:09 hald-addon-stor
 4685 ?        00:00:01 hald-addon-stor
 4687 ?        00:00:00 hald-addon-stor
 4691 ?        00:00:00 cupsd
 4790 ?        00:00:00 avahi-daemon
 4791 ?        00:00:00 avahi-daemon
 4805 ?        00:00:00 dhcdbd
 4825 ?        00:00:00 hcid
 4836 ?        00:00:00 bluetoothd-serv
 4837 ?        00:00:00 bluetoothd-serv
 4840 ?        00:00:00 krfcommd
 4873 ?        00:00:00 atd
 4887 ?        00:00:00 cron
 4988 ?        00:00:00 x-session-manag
 5031 ?        00:00:00 ssh-agent
 5064 ?        00:00:00 start_kdeinit
 5065 ?        00:00:00 kdeinit
 5068 ?        00:00:00 dcopserver
 5071 ?        00:00:00 klauncher
 5073 ?        00:00:02 kded
 5078 ?        00:00:01 kwrapper
 5080 ?        00:00:00 ksmserver
 5081 ?        00:00:10 kwin
 5083 ?        00:00:07 kdesktop
 5085 ?        00:00:28 kicker
 5089 ?        00:00:00 kio_uiserver
 5104 ?        00:00:10 artsd
 5107 ?        00:00:01 kaccess
 5112 ?        00:00:01 kmix
 5114 ?        00:00:00 katapult
 5115 ?        00:00:44 d3lphin
 5117 ?        00:00:01 kdesu
 5119 ?        00:00:00 knotify
 5122 ?        00:00:28 d3lphin
 5123 ?        00:00:17 pidgin
 5127 ?        00:00:00 dbus-launch
 5128 ?        00:00:00 dbus-daemon
 5130 ?        00:00:01 konqueror
 5139 ?        00:00:00 aspell
 5140 ?        00:00:01 konqueror
 5143 ?        00:00:00 knetworkmanager
 5150 ?        00:00:00 klipper
 5166 ?        00:00:00 kdeinit
 5171 ?        00:00:00 dcopserver
 5176 ?        00:00:00 klauncher
 5179 ?        00:00:00 kded
 5194 ?        00:00:00 kio_file
 5267 ?        00:00:00 firefox
 5279 ?        00:00:00 run-mozilla.sh
 5283 ?        00:30:34 firefox-bin
 5292 ?        00:00:00 gconfd-2
 5346 ?        00:00:00 dhclient
 5595 ?        00:00:00 knotify
 5598 ?        00:00:14 artsd
 6175 ?        00:00:24 kate
10825 pts/2    00:00:00 bash
10854 ?        00:00:18 d3lphin
10859 ?        00:00:00 kio_file
10911 ?        00:48:37 ksysguard
10912 ?        00:00:00 sh
10913 ?        00:13:57 ksysguardd
28526 ?        00:00:00 konsole
28527 pts/3    00:00:00 bash
28547 pts/3    00:00:00 ps

```

---

### Post by taurus on 2007-12-08
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by tOaDeR2005 on 2007-12-08
the first command:

```
sudo apt-get update
[sudo] password for toader:
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Hit http://us.archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 3B in 1s (2B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```


and:


```
sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

---

### Post by taurus on 2007-12-08
Try

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by tOaDeR2005 on 2007-12-11
worked!! thank you very much. sorry i took so long to thank you.

---

