---
title: "Errors were encountered while processing"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by onurguzel on 2006-07-22
```
$sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages will be REMOVED
  gsfonts-x11
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 119kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 69509 files and directories currently installed.)
Removing gsfonts-x11 ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: error processing gsfonts-x11 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 gsfonts-x11
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
What's the matter? and the solution? ](*,)

---

### Post by onurguzel on 2006-07-22
```
$sudo aptitude install mozilla-thunderbird

...

E: I wasn't able to locate file for the gsfonts-x11 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
```

---

### Post by taurus on 2006-07-22
Maybe you have apt-get running in the background somewhere.  What is the output of this command from a terminal?

```

ps -A

```

---

### Post by onurguzel on 2006-07-22
```
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
   10 ?        00:00:00 kacpid-work-0
  152 ?        00:00:00 pdflush
  153 ?        00:00:00 pdflush
  155 ?        00:00:00 aio/0
  154 ?        00:00:00 kswapd0
  742 ?        00:00:00 kseriod
 1754 ?        00:00:05 ata/0
 1755 ?        00:00:00 ata_hotplug/0
 1760 ?        00:00:00 scsi_eh_0
 1761 ?        00:00:00 scsi_eh_1
 1826 ?        00:00:00 khubd
 1844 ?        00:00:00 khpsbpkt
 1874 ?        00:00:00 knodemgrd_0
 1949 ?        00:00:00 kjournald
 2182 ?        00:00:00 udevd
 3116 ?        00:00:00 pccardd
 3138 ?        00:00:00 ipw2200/0
 3586 ?        00:00:00 dhclient3
 3936 ?        00:00:00 acpid
 4024 ?        00:00:00 syslogd
 4050 ?        00:00:00 dd
 4052 ?        00:00:00 klogd
 4077 ?        00:00:00 hpiod
 4080 ?        00:00:00 python
 4128 ?        00:00:00 cupsd
 4162 ?        00:00:00 dbus-daemon
 4177 ?        00:00:01 hald
 4178 ?        00:00:00 hald-runner
 4183 ?        00:00:00 hald-addon-acpi
 4233 ?        00:00:00 hald-addon-keyb
 4247 ?        00:00:00 hald-addon-stor
 4248 ?        00:00:00 hald-addon-stor
 4297 ?        00:00:00 mysqld_safe
 4361 ?        00:00:00 mysqld
 4362 ?        00:00:00 logger
 4444 ?        00:00:00 powernowd
 4498 ?        00:00:00 hcid
 4504 ?        00:00:00 sdpd
 4513 ?        00:00:00 krfcommd
 4526 ?        00:00:00 mdadm
 4561 ?        00:00:00 atd
 4574 ?        00:00:00 cron
 4943 ?        00:00:00 kdm
 4993 tty1     00:00:00 getty
 4994 tty2     00:00:00 getty
 4995 tty3     00:00:00 getty
 4996 tty4     00:00:00 getty
 4997 tty5     00:00:00 getty
 4998 tty6     00:00:00 getty
 5011 tty7     00:01:07 Xorg
 5012 ?        00:00:00 kdm
 5046 ?        00:00:00 startkde
 5083 ?        00:00:00 ssh-agent
 5086 ?        00:00:00 dbus-launch
 5087 ?        00:00:00 dbus-daemon
 5116 ?        00:00:00 kdeinit
 5119 ?        00:00:00 dcopserver
 5121 ?        00:00:00 klauncher
 5123 ?        00:00:05 kded
 5125 ?        00:00:00 gam_server
 5132 ?        00:00:05 artsd
 5134 ?        00:00:00 kaccess
 5135 ?        00:00:00 kwrapper
 5137 ?        00:00:00 ksmserver
 5142 ?        00:00:01 kwin
 5144 ?        00:00:01 kdesktop
 5146 ?        00:00:02 kicker
 5149 ?        00:00:00 kbluetoothd
 5151 ?        00:00:05 adept_notifier
 5152 ?        00:00:00 klipper
 5156 ?        00:00:00 kio_file
 5158 ?        00:00:00 kio_uiserver
 5169 ?        00:00:00 kmix
 5170 ?        00:00:00 katapult
 5175 ?        00:00:00 dhclient3
 5182 ?        00:00:00 knotify
 5186 ?        00:00:00 kdesud
 5277 ?        00:00:39 konqueror
 5288 ?        00:00:00 kio_http
 5289 ?        00:00:00 kio_http
 5351 ?        00:00:00 kio_http
 5427 ?        00:00:00 kio_http
 5581 ?        00:00:01 konsole
 5582 pts/1    00:00:00 bash
 5669 ?        00:00:00 kio_http
 5757 ?        00:00:00 kio_http
 5835 ?        00:00:00 kio_http
 5884 pts/1    00:00:00 ps

```

---

### Post by taurus on 2006-07-22
Try running it again and see what happens...

```

sudo aptitude update
sudo aptitude install mozilla-thunderbird

```
Otherwise, try installing it with synaptic...

---

### Post by onurguzel on 2006-07-22
I've sent SIGKILL to adept_notifier and now it seem to be right (or i think so)

---

### Post by onurguzel on 2006-07-22
```
Fetched 10.3MB in 3m27s (49.6kB/s)
Preconfiguring packages ...
(Reading database ... 69509 files and directories currently installed.)
Removing gsfonts-x11 ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: error processing gsfonts-x11 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 gsfonts-x11
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by onurguzel on 2006-07-22
in addition:
```
bash: synaptic: command not found
```

---

### Post by taurus on 2006-07-22
You access synaptic from System -> Administrations!!!

---

### Post by onurguzel on 2006-07-22
There aren't any menus like that?

---

### Post by taurus on 2006-07-22
Just looked at your "ps -A" again and I see that you are using KDE as your window manager instead of Gnome.  Since I don't have access to a KDE right now, just browse around in the K menu and see if you can find it.  Otherwise, see if you can find it from a prompt.

```

sudo find / -name synaptic -print

```

---

### Post by onurguzel on 2006-07-22
I think I've made a mistake on installing(installed today) and will try to reinstall... Thanks for patience.

---

### Post by onurguzel on 2006-07-23
I've reinstalled and everything goes right... Thanks

---

### Post by elfgoh on 2006-10-28
> **onurguzel said:**
> ```

usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: error processing gsfonts-x11 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 gsfonts-x11
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
What's the matter? and the solution? ](*,)

Hi, this should be a more elegant solution from [http://ubuntuforums.org/showthread.php?t=213711](http://ubuntuforums.org/showthread.php?t=213711)

Just change 

**update-fonts-dir --x11r7-layout misc**

to 

**update-fonts-dir misc**

Then reinstall the package

HTH

---

