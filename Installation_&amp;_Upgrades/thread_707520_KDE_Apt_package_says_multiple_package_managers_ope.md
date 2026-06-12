---
title: "KDE Apt package says multiple package managers open."
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by VoiceOvGod on 2008-02-25
Trying to repair some packages in the package manager (Attempted upgrade from 7.04 to 7.10 that failed) - Cannot reinstall because CD drive is toast, and cannot boot from USB.

Crash handler says this:

```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1235486512 (LWP 5712)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb661a875 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb661c201 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb68256e0 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb6822f65 in ?? () from /usr/lib/libstdc++.so.6
#11 0xb6822fa2 in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb68230ca in __cxa_throw () from /usr/lib/libstdc++.so.6
#13 0x0812b916 in ?? ()
#14 0x0812be8a in ?? ()
#15 0x0812bee8 in ?? ()
#16 0x0812c735 in ?? ()
#17 0x0812a22d in ?? ()
#18 0x08114379 in ?? ()
#19 0x080951ed in ?? ()
#20 0x0807378d in ?? ()
#21 0x0807408e in ?? ()
#22 0xb6e6a893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb71f68ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#24 0xb6e8a842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#25 0xb6e92258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#26 0xb6e01af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#27 0xb6e0391f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#28 0xb75c7ca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#29 0xb6d94209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#30 0xb6df453b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#31 0xb6da8d49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#32 0xb6e1c1ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#33 0xb6e1bfde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#34 0xb6e03699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#35 0x0806f75e in ?? ()
#36 0xb6606050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#37 0x0806f401 in ?? ()

```

Also, here are the currently running processes:

```

~$ ps -A
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
  116 ?        00:00:00 kseriod
  135 ?        00:00:00 pdflush
  136 ?        00:00:00 pdflush
  137 ?        00:00:00 kswapd0
  138 ?        00:00:00 aio/0
 2203 ?        00:00:00 ksuspend_usbd
 2204 ?        00:00:00 khubd
 2222 ?        00:00:00 khpsbpkt
 2224 ?        00:00:00 knodemgrd_0
 2232 ?        00:00:00 ata/0
 2233 ?        00:00:00 ata_aux
 2236 ?        00:00:00 scsi_eh_0
 2237 ?        00:00:00 scsi_eh_1
 2371 ?        00:00:00 scsi_eh_2
 2372 ?        00:00:00 usb-storage
 2545 ?        00:00:00 kjournald
 2755 ?        00:00:00 udevd
 3583 ?        00:00:00 pccardd
 3593 ?        00:00:00 pccardd
 3626 ?        00:00:00 kpsmoused
 4025 ?        00:00:00 dhclient3
 4109 ?        00:00:00 kjournald
 4438 tty4     00:00:00 getty
 4439 tty5     00:00:00 getty
 4442 tty2     00:00:00 getty
 4443 tty3     00:00:00 getty
 4444 tty1     00:00:00 getty
 4445 tty6     00:00:00 getty
 4706 ?        00:00:00 acpid
 4804 ?        00:00:00 syslogd
 4857 ?        00:00:00 dd
 4859 ?        00:00:00 klogd
 4880 ?        00:00:00 dbus-daemon
 4896 ?        00:00:00 NetworkManager
 4909 ?        00:00:00 NetworkManagerD
 4929 ?        00:00:01 hald
 4930 ?        00:00:00 hald-runner
 4974 ?        00:00:00 kdm
 4981 tty7     00:00:36 Xorg
 4997 ?        00:00:00 hald-addon-keyb
 4999 ?        00:00:00 hald-addon-cpuf
 5000 ?        00:00:00 hald-addon-acpi
 5001 ?        00:00:00 hald-addon-keyb
 5002 ?        00:00:00 hald-addon-keyb
 5010 ?        00:00:00 kdm
 5017 ?        00:00:00 hald-addon-stor
 5046 ?        00:00:00 cupsd
 5083 ?        00:00:00 mysqld_safe
 5123 ?        00:00:00 mysqld
 5124 ?        00:00:00 logger
 5264 ?        00:00:00 hald-addon-keyb
 5268 ?        00:00:00 hald-addon-keyb
 5294 ?        00:00:00 kondemand/0
 5338 ?        00:00:00 hcid
 5355 ?        00:00:00 krfcommd
 5358 ?        00:00:00 bluetoothd-serv
 5378 ?        00:00:00 bluetoothd-serv
 5393 ?        00:00:00 atd
 5407 ?        00:00:00 cron
 5514 ?        00:00:00 x-session-manag
 5557 ?        00:00:00 ssh-agent
 5592 ?        00:00:00 start_kdeinit
 5593 ?        00:00:00 kdeinit
 5596 ?        00:00:00 dcopserver
 5599 ?        00:00:00 klauncher
 5601 ?        00:00:03 kded
 5606 ?        00:00:00 kwrapper
 5608 ?        00:00:00 ksmserver
 5609 ?        00:00:03 kwin
 5611 ?        00:00:03 kdesktop
 5613 ?        00:00:05 kicker
 5614 ?        00:00:00 kio_file
 5630 ?        00:00:06 artsd
 5633 ?        00:00:00 kaccess
 5637 ?        00:00:01 kmix
 5639 ?        00:00:00 konqueror
 5640 ?        00:00:00 konqueror
 5648 ?        00:00:03 guidance-power-
 5656 ?        00:00:00 klipper
 5657 ?        00:00:00 kblueplugd
 5660 ?        00:00:00 knetworkmanager
 5662 ?        00:00:01 konqueror
 5670 ?        00:00:00 firefox
 5682 ?        00:00:00 run-mozilla.sh
 5686 ?        00:00:51 firefox-bin
 5694 ?        00:00:00 gconfd-2
 5715 ?        00:00:00 kdeinit
 5720 ?        00:00:00 dcopserver
 5723 ?        00:00:00 klauncher
 5725 ?        00:00:03 kded
 5731 ?        00:00:00 knotify
 5734 ?        00:00:05 artsd
 5736 ?        00:00:03 konsole
 5737 pts/2    00:00:00 bash
 5775 ?        00:00:00 knotify
 5786 ?        00:00:00 scsi_eh_3
 5787 ?        00:00:00 usb-storage
 5820 ?        00:00:00 hald-addon-stor
 5852 ?        00:00:00 kio_file
 5853 ?        00:00:00 kio_file
 5856 ?        00:00:00 kio_file
 5880 ?        00:00:00 kio_uiserver
 5960 pts/2    00:00:00 ps

```

---

### Post by jeffus_il on 2008-02-25
Try <ctrl><alt><f1> to a console
Stop gdm or kdm  ```
sudo /etc/init.d/kdm stop
```run ```
sudo aptitude update
```and then ```
sudo aptitude upgrade
```

---

### Post by VoiceOvGod on 2008-02-25
Aight, I was able to get to the CLI, however, the resolution on it is so horrible. It's like it is showing only part of the screen.

Tried Console Login as well. It sat there, then reverted to the GUI login.

Is there a way to adjust the resolution?

---

### Post by VoiceOvGod on 2008-02-25
ran the

```

sudo dpkg --configure -a

```

Got the following:

```

Errors were encountered while processing:
 acpid
 acpid-support
 powermanagement-interface
 kubuntu-desktop

```

---

### Post by VoiceOvGod on 2008-02-25
Ok, did the upgrade

The above packages could not be upgraded though.

I was told this:

```

Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1] file and follow its instructions.

/usr/share/doc/grub/NEWS.Debian.gz

```

This appeared for a couple items.

---

### Post by VoiceOvGod on 2008-02-25
I also attempted

```
sudo dpkg --configure acpid
```

and got the following:

```
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid

```

---

### Post by VoiceOvGod on 2008-02-25
Looks like the steps you gave me worked to get me back into the PM. Thanks

---

