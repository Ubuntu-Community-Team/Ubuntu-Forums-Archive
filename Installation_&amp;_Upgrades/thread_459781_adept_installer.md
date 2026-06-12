---
title: "adept installer"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by Pyranima on 2007-05-31
whenever i try to use adept installer or anything with adept it gives the following message:

Database Locked-adept installer
another process is using the packaging system database (probably some other adept application or apt-get or aptitude). please close the other application before using this one.






How do i close it when i dont even know what the program running is (though i am pretty sure it is adept package manager). how do i "endtask" or unlock the adept

---

### Post by nereid on 2007-05-31
Open a terminal and enter

```

ps ax

```

Look for the adept, apt-get or aptitude applications. If anyone of this applications is running the apt database is locked. To regain access kill the specified process with the kill command

```

kill [pid] // where pid is the number in the front

or

killall apt-get // to kill all processes called apt-get

```

---

### Post by Pyranima on 2007-06-01
it didnt work this is what i get

fnx@fnx-laptop:~$ killall apt-get
apt-get: no process killed
fnx@fnx-laptop:~$ killall apt-get//
apt-get//: No such file or directory
fnx@fnx-laptop:~$ kill all apt-get
bash: kill: all: arguments must be process or job IDs
bash: kill: apt-get: arguments must be process or job IDs
fnx@fnx-laptop:~$ kill [5188]
bash: kill: [5188]: arguments must be process or job IDs
fnx@fnx-laptop:~$ killall apt-get
apt-get: no process killed
fnx@fnx-laptop:~$ kill [5188 ?]
bash: kill: [5188: arguments must be process or job IDs
bash: kill: ?]: arguments must be process or job IDs
fnx@fnx-laptop:~$ killall apt-get
apt-get: no process killed
fnx@fnx-laptop:~$
fnx@fnx-laptop:~$
fnx@fnx-laptop:~$ kill [adept_notifier]
bash: kill: [adept_notifier]: arguments must be process or job IDs
fnx@fnx-laptop:~$    







 PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:00 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S<     0:00 [events/0]
    6 ?        S<     0:00 [khelper]
    7 ?        S<     0:00 [kthread]
   30 ?        S<     0:00 [kblockd/0]
   31 ?        S<     0:00 [kacpid]
   32 ?        S<     0:00 [kacpi_notify]
  117 ?        S<     0:00 [kseriod]
  138 ?        S      0:00 [pdflush]
  139 ?        S      0:00 [pdflush]
  140 ?        S<     0:00 [kswapd0]
  141 ?        S<     0:00 [aio/0]
 1943 ?        S<     0:00 [ata/0]
 1944 ?        S<     0:00 [ata_aux]
 1947 ?        S<     0:00 [scsi_eh_0]
 1948 ?        S<     0:00 [scsi_eh_1]
 1950 ?        S<     0:00 [ksuspend_usbd]
 1951 ?        S<     0:00 [khubd]
 2206 ?        S<     0:00 [kjournald]
 2405 ?        S<s    0:00 /sbin/udevd --daemon
 3227 ?        S<     0:00 [kpsmoused]
 3329 ?        S<     0:00 [pccardd]
 3425 ?        S<     0:00 [hda_codec]
 4079 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4080 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4083 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4084 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4085 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4086 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4332 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 4429 ?        Ss     0:00 /sbin/syslogd
 4481 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4483 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4504 ?        Ss     1:34 /usr/bin/dbus-daemon --system
 4520 ?        Ss     0:10 /usr/sbin/hald
 4521 ?        S      0:00 hald-runner
 4528 ?        S      0:00 hald-addon-acpi: listening on acpid socket /var/run/a
 4537 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event1
 4546 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event4
 4549 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event5
 4558 ?        D      0:07 hald-addon-storage: polling /dev/hdc
 4575 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 4590 ?        Ssl    0:20 /usr/sbin/NetworkManager --pid-file /var/run/NetworkM
 4608 ?        Ss     0:00 avahi-daemon: registering [fnx-laptop.local]
 4609 ?        Ss     0:00 avahi-daemon: chroot helper
 4625 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/ru
 4710 ?        Ss     0:00 /usr/sbin/hpiod
 4713 ?        S      0:00 python /usr/sbin/hpssd
 4828 ?        Ss     0:00 /usr/sbin/hcid -x -s
 4845 ?        S<     0:00 [krfcommd]
 4881 ?        Ss     0:00 /usr/sbin/atd
 4895 ?        Ss     0:00 /usr/sbin/cron
 4954 ?        Ss     0:00 /usr/bin/kdm
 4973 tty7     Ss+   32:25 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xa
 4988 ?        S      0:00 -:0
 5040 ?        Ss     0:00 /bin/sh /usr/bin/x-session-manager
 5087 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 5090 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-ma
 5091 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-add
 5126 ?        S      0:00 start_kdeinit --new-startup +kcminit_startup
 5127 ?        Ss     0:00 kdeinit Running...
 5130 ?        S      0:24 dcopserver [kdeinit] --nosid
 5133 ?        S      0:00 klauncher [kdeinit] --new-startup
 5135 ?        S      0:20 kded [kdeinit] --new-startup
 5140 ?        S      0:00 kwrapper ksmserver
 5142 ?        S      0:00 ksmserver [kdeinit]
 5143 ?        S      0:06 kwin [kdeinit]
 5145 ?        S      0:03 kdesktop [kdeinit]
 5147 ?        S      3:04 kicker [kdeinit]
 5151 ?        S      0:00 kio_uiserver [kdeinit]
 5166 ?        SLl    0:01 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c
 5168 ?        S      0:00 kaccess [kdeinit]
 5173 ?        S      0:05 /usr/bin/python /usr/share/python-support/kde-guidanc
 5175 ?        S      0:00 konqueror [kdeinit] --preload
 5176 ?        S      0:00 knotify [kdeinit]
 5178 ?        S      0:00 konqueror [kdeinit] --preload
 5180 ?        S      0:00 kbluetoothd --dontforceshow
 5182 ?        S      2:30 knetworkmanager [kdeinit]
 5185 ?        S      0:00 /usr/bin/passkey-agent --default /usr/lib/kdebluetoot
 5187 ?        S      0:00 klipper [kdeinit]
 5188 ?        S      0:02 adept_notifier
 5212 ?        Ss     0:00 avahi-autoipd: [eth0] bound 169.254.6.16
 5213 ?        Ss     0:00 avahi-autoipd: [eth0] callout dispatcher
 5285 ?        S      0:00 /sbin/wpa_supplicant -dd -g /var/run/wpa_supplicant-g
 5292 ?        S      0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.ath0.le
 5344 ?        S      0:00 kwalletmanager --kwalletd
 5491 ?        Sl     5:45 /usr/lib/firefox/firefox-bin
 5500 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 11
 5571 ?        S      0:00 /bin/sh /usr/lib/openoffice/program/soffice -writer -
 5586 ?        Sl     0:18 /usr/lib/openoffice/program/soffice.bin -writer -spla
 5762 ?        S      0:00 kio_file [kdeinit] file /tmp/ksocket-fnx/klauncherSs3
 6013 ?        SNs    0:00 /usr/sbin/cupsd
 6293 ?        S      0:00 konsole [kdeinit]
 6294 pts/1    Ss     0:00 /bin/bash
 6310 pts/1    R+     0:00 ps ax

---

### Post by Pyranima on 2007-06-01
can anyone help?

---

### Post by rillip on 2007-06-01
This error usually occurs when any combination (two or more) of Synatpic, Add/Remove Programs, Adept, apt, or Apt-get are running.  Looking at the ps aux, I don't see any of these in particular.  If you're sure this is true, then you can just close the program, delete the lockfile, and try again.  I believe it's in /var/lib/dpkg/lock

---

### Post by Pyranima on 2007-06-02
how do i delete it

---

### Post by Pyranima on 2007-06-02
can no one help me delete this thing? or figure out how to fix it?

---

### Post by Pyranima on 2007-06-04
I figured out it crashed while i was using adept manager can someone help me fix it

---

### Post by nereid on 2007-06-04
If the lock isn't set, the lock file should be empty. Start your favorite editor as root and delete the content of the /var/lib/dpkg/lock file. Then everything should be allright.

---

### Post by standvm on 2007-06-28
I tried to find the lock file :              /var/lib/dpkg/lock  but it does not allow me to delete this lock file. Is there another way of unlocking the adept database? Please help.

---

### Post by Flybersite on 2007-11-01
- Open up konsole
- type: cd /var/lib/dpkg
- type: rm lock

Now it should be removed, even though I have the same problem and it keeps yelling that there's another process running

---

### Post by slack on 2007-12-03
I've been having the same problem ever since I upgraded from 7.04 to 7.10.  I've tried removing the lockfile at /var/lib/dpkg/lock but the problem persists (an empty lockfile is recreated the next time adept is run, I'm not quite sure exactly what the "heallthy" behaviour is -- should there always be a lockfile there if the adept daemon is running in the background or only when it's actively doing something?).  I've checked ps ax for any sign of apt and can't see anything likely.

If anybody has any more ideas then I'd be grateful.

---

### Post by BrianElliott0218 on 2008-01-02
> **Flybersite said:**
> - Open up konsole
- type: cd /var/lib/dpkg
- type: rm lock

Now it should be removed, even though I have the same problem and it keeps yelling that there's another process running

Great!  But how do I get permissions to remove that (I am getting "permission denied" due to not being root)
:confused:
Sorry, rank beginner in Linux...
Looks like this fix will do it, just have to figure out how to get permissions.

In addition (since I like skinning cats in more than one way) is there a way to get permissions when using Konquerer in the GUI instead of going command line in Konsole?  This would simply be an alternative if it's possible.

Thanks!

---

### Post by BrianElliott0218 on 2008-01-02
> **Flybersite said:**
> - Open up konsole
- type: cd /var/lib/dpkg
- type: rm lock

Now it should be removed, even though I have the same problem and it keeps yelling that there's another process running

Flybersite's solutions didn't work, even as admin...
 But this worked for me:
sudo dpkg --configure -a


I was able to get into the apt-get / adept applications afterward.  All seems well so far...:)
~BE

---

### Post by dewcansam on 2008-01-27
I was having problems with this too. Adept just crashed during an install of the jre. Tried removing the lock file as suggested, without any results. But using BrianElliott0218's instructions got me close. Here is how i solved my issue.

First open up a terminal window by going "System >> Konsole" . The run these commands
```

$ sudo dpkg --configure -a

```
This will pick up where adept crashed / left off and finish the installs. Trying to run adept after this still left me with nothing. Adept now crashed with no warning. Then i ran
```

$ sudo dpkg --configure -a
## dpkg outputed errors here , hmmm thats why adept would crash and not display anything 
## so note the errors 
## since adept died while trying to install jre thats what my errors relate too
## so try this now
$ sudo apt-get install j2re1.4 j2re1.4-mozilla-plugin
## now run the dpkg line again
$ sudo dpkg --configure -a
$ 
## great !! no errors anymore

```

now running "System >> Adept Manager" went smoothly 
:guitar:

---

