---
title: "Cannot use adept"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by mmaslowsky on 2007-07-08
I'm running Kubuntu 7.04 and every time I run adept I get an error message saying:

Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

I have tried rebooting the system, and I've used top to try to find any already running processes that might be interfering with adept, but I can't find any.

---

### Post by taurus on 2007-07-08
Are you sure you don't have anything like synaptic/apt-get/aptitude running in the background?  

What's the output of this command from a terminal?

```
ps -A
```

---

### Post by mmaslowsky on 2007-07-08
The output of ls -A is:

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
   30 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kacpid
   32 ?        00:00:00 kacpi_notify
  157 ?        00:00:00 kseriod
  178 ?        00:00:00 pdflush
  179 ?        00:00:00 pdflush
  180 ?        00:00:00 kswapd0
  181 ?        00:00:00 aio/0
 1986 ?        00:00:00 ksuspend_usbd
 1987 ?        00:00:00 khubd
 2119 ?        00:00:00 ata/0
 2120 ?        00:00:00 ata_aux
 2149 ?        00:00:00 scsi_eh_0
 2150 ?        00:00:00 scsi_eh_1
 2357 ?        00:00:00 kjournald
 2556 ?        00:00:00 udevd
 3456 ?        00:00:00 kpsmoused
 3511 ?        00:00:00 pccardd
 3512 ?        00:00:00 ipw2200/0
 4498 ?        00:00:00 acpid
 4592 ?        00:00:00 syslogd
 4648 ?        00:00:00 dd
 4650 ?        00:00:00 klogd
 4671 ?        00:00:01 dbus-daemon
 4687 ?        00:00:02 hald
 4688 ?        00:00:00 hald-runner
 4694 ?        00:00:00 hald-addon-acpi
 4695 ?        00:00:00 hald-addon-cpuf
 4696 ?        00:00:00 hald-addon-usb-
 4703 ?        00:00:00 hald-addon-keyb
 4706 ?        00:00:00 hald-addon-keyb
 4709 ?        00:00:00 hald-addon-keyb
 4712 ?        00:00:00 hald-addon-keyb
 4715 ?        00:00:00 hald-addon-keyb
 4740 ?        00:00:00 hald-addon-stor
 4753 ?        00:00:00 dhcdbd
 4768 ?        00:00:00 NetworkManager
 4786 ?        00:00:00 avahi-daemon
 4787 ?        00:00:00 avahi-daemon
 4800 ?        00:00:00 NetworkManagerD
 4856 ?        00:00:00 cupsd
 4880 ?        00:00:00 hpiod
 4883 ?        00:00:00 python
 4997 ?        00:00:00 kondemand/0
 5014 ?        00:00:00 nmbd
 5016 ?        00:00:00 smbd
 5060 ?        00:00:00 smbd
 5061 ?        00:00:00 hcid
 5078 ?        00:00:00 krfcommd
 5114 ?        00:00:00 atd
 5128 ?        00:00:00 cron
 5210 ?        00:00:00 kdm
 5243 tty7     00:00:35 Xorg
 5244 ?        00:00:00 kdm
 5260 ?        00:00:00 x-session-manag
 5301 ?        00:00:00 ssh-agent
 5304 ?        00:00:00 dbus-launch
 5305 ?        00:00:00 dbus-daemon
 5340 ?        00:00:00 start_kdeinit
 5341 ?        00:00:00 kdeinit
 5349 ?        00:00:00 avahi-autoipd
 5350 ?        00:00:00 avahi-autoipd
 5352 ?        00:00:00 dcopserver
 5355 ?        00:00:00 klauncher
 5357 ?        00:00:00 kded
 5362 ?        00:00:00 kwrapper
 5364 ?        00:00:00 ksmserver
 5365 ?        00:00:01 kwin
 5367 ?        00:00:01 kdesktop
 5369 ?        00:00:02 kicker
 5388 ?        00:00:03 artsd
 5392 ?        00:00:00 kaccess
 5396 ?        00:00:00 konqueror
 5404 ?        00:00:00 knotify
 5405 ?        00:00:01 guidance-power-
 5412 ?        00:00:00 konqueror
 5413 ?        00:00:00 klipper
 5415 ?        00:00:00 dhclient3
 5426 ?        00:00:00 kbluetoothd
 5428 ?        00:00:00 passkey-agent
 5433 ?        00:00:00 knetworkmanager
 5437 ?        00:00:00 wpa_supplicant
 5449 ?        00:00:00 dhclient
 5514 ?        00:00:00 kdesud
 5555 ?        00:00:03 artsd
 5583 ?        00:00:03 konsole
 5584 pts/1    00:00:00 bash
 5736 ?        00:00:37 firefox-bin
 5745 ?        00:00:00 gconfd-2
 5819 ?        00:00:00 kmix
 5821 ?        00:00:00 kaffeine
 5822 ?        00:00:00 kio_file
 5831 tty4     00:00:00 getty
 5837 tty5     00:00:00 getty
 5843 tty2     00:00:00 getty
 5849 tty3     00:00:00 getty
 5860 tty1     00:00:00 getty
 5866 tty6     00:00:00 getty
 5870 pts/1    00:00:00 ps

---

### Post by taurus on 2007-07-08
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by bapoumba on 2007-07-08
In addition to what taurus suggested (hi taurus :)) please try:
```
sudo dpkg --configure -a
```

---

### Post by mmaslowsky on 2007-07-08
aptitude update errors out with this:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

dpgk --configure -a returns:
Errors were encountered while processing:
 j2re1.4-mozilla-plugin

---

### Post by bapoumba on 2007-07-08
> **mmaslowsky said:**
> aptitude update errors out with this:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

dpgk --configure -a returns:
Errors were encountered while processing:
 j2re1.4-mozilla-plugin
How did you install that package? Do you have the multiverse repositories enabled?

---

### Post by mmaslowsky on 2007-07-08
I installed that package using adept, which now says that package is broken.  I am not using the multiverse (or any other third party repositories).

---

### Post by bapoumba on 2007-07-08
```
~$ aptitude show j2re1.4-mozilla-plugin
Package: j2re1.4-mozilla-plugin
State: not installed
Version: 1:0ubuntu6
Priority: optional
Section: multiverse/web
```
The package is in the multiverse repository. Please enable this repo and run again:
```
sudo aptitude update
sudo aptitude upgrade
```
Or remove the package if you do not need the java plugin for firefox.

---

### Post by mmaslowsky on 2007-07-08
I tried to remove the package using the following command:

sudo aptitude remove j2re1.4-mozilla-plugin 

and I received the following error:

Writing extended state information... Error!
E: I wasn't able to locate a file for the ksame package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

---

### Post by bapoumba on 2007-07-08
Hmm, could you post your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by mmaslowsky on 2007-07-08
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted univ                                                              erse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted                                                               universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by bapoumba on 2007-07-09
> **mmaslowsky said:**
> #
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe [COLOR="Green"]multiverse[/COLOR]
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe [COLOR="Green"]multiverse[/COLOR]

Please add the multiverse repositories to that line (I marked them in green), and paste the output to:
```
sudo aptitude update
```

---

### Post by mmaslowsky on 2007-07-09
I fixed this problem.  As it turns out, I wasn't responding correctly to Sun's EULA for java, which was causing the broken package.

Thanks for your help.

---

