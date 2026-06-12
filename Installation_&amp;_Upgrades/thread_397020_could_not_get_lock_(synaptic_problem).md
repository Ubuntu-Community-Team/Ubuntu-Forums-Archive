---
title: "could not get lock (synaptic problem)"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by gc1 on 2007-03-30
I get this error message if I try to use Synaptic:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
......no other process is using it but I had an interrupted download days ago. 

I get another message as well, telling me to use this command:
dpkg --configure -a
When I do so there is no change

---

### Post by albesan on 2007-03-30
hey, "what's the output of dpkg --configure -a"
if any.

a.

---

### Post by gc1 on 2007-03-30
thanks for your interest. The result varies, depending on what packages I recently opened. I've done the command just now with the reply

dpkg: status database area is locked by another process

Strange answer because I don't have much running

Graham

---

### Post by zvacet on 2007-03-31
It is telling you that you run somethig else in the same time.Is it update manager or automatix maybe?And try 
```
sudo dpkg --configure -a 
```

---

### Post by gc1 on 2007-03-31
The following command was the one I was told to use at the time when I first got Synaptic troubles. An install got stopped and when I used this command the problem remained. Synaptic was hung, I had to shut down the sysatem and since then Synaptic has not worked properly.
This is the outcome of the command after a fresh start-up

 sudo dpkg --configure -a
Password:
Setting up openoffice.org-help-en-gb (2.0.4-0ubuntu1) ...

Setting up update-manager (0.45.2) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 484 strings at 20 - 2848
Wrote aliases at 2848 - 29fc
Wrote parents at 29fc - 33cc
Wrote literal globs at 33cc - 3430
Wrote suffix globs at 3430 - 68a8
Wrote full globs at 68a8 - 68cc
Wrote magic at 68cc - bfb8
Wrote namespace list at bfb8 - bfc8
***

Thanks
 Graham

---

### Post by unisol on 2007-03-31
make sure its the only package manager that is running.

---

### Post by gc1 on 2007-04-01
I think there's no other package manager running but the system acts as if there is.  I guess the following is a reliable way of knowing what is running:

gra@localhost:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
   10 ?        00:00:00 kacpi_notify
  102 ?        00:00:00 kseriod
  135 ?        00:00:00 pdflush
  137 ?        00:00:00 kswapd0
  138 ?        00:00:00 aio/0
 1674 ?        00:00:00 ata/0
 1771 ?        00:00:00 khubd
 1904 ?        00:00:00 kjournald
 1977 ?        00:00:00 logd
 2130 ?        00:00:00 udevd
 2877 ?        00:00:00 shpchpd
 2927 ?        00:00:00 kpsmoused
 2958 ?        00:00:00 kgameportd
 3305 ?        00:00:00 dhclient3
 3383 ?        00:00:00 kjournald
 3477 ?        00:00:00 portmap
 3656 tty1     00:00:00 getty
 3657 tty2     00:00:00 getty
 3658 tty3     00:00:00 getty
 3659 tty4     00:00:00 getty
 3660 tty5     00:00:00 getty
 3661 tty6     00:00:00 getty
 3851 ?        00:00:00 acpid
 3961 ?        00:00:00 dd
 3963 ?        00:00:00 klogd
 3982 ?        00:00:00 dbus-daemon
 3997 ?        00:00:01 hald
 3998 ?        00:00:00 hald-runner
 4004 ?        00:00:00 hald-addon-acpi
 4008 ?        00:00:00 hald-addon-keyb
 4021 ?        00:00:00 hald-addon-stor
 4039 ?        00:00:00 perl
 4114 ?        00:00:00 gdm
 4121 ?        00:00:00 gdm
 4124 tty7     00:00:10 Xorg
 4243 ?        00:00:00 freshclam
 4255 ?        00:00:00 x-session-manag
 4305 ?        00:00:00 ssh-agent
 4306 ?        00:00:00 ssh-agent
 4317 ?        00:00:00 dbus-launch
 4336 ?        00:00:00 dbus-daemon
 4361 ?        00:00:01 gconfd-2
 4493 ?        00:00:00 nfsd4
 4494 ?        00:00:00 nfsd
 4495 ?        00:00:00 nfsd
 4496 ?        00:00:00 nfsd
 4497 ?        00:00:00 nfsd
 4498 ?        00:00:00 lockd
 4499 ?        00:00:00 rpciod/0
 4500 ?        00:00:00 nfsd
 4501 ?        00:00:00 nfsd
 4502 ?        00:00:00 nfsd
 4503 ?        00:00:00 nfsd
 4507 ?        00:00:00 gnome-keyring-d
 4510 ?        00:00:00 gnome-settings-
 4512 ?        00:00:00 rpc.mountd
 4551 ?        00:00:00 nmbd
 4555 ?        00:00:00 smbd
 4609 ?        00:00:00 smbd
 4610 ?        00:00:00 rpc.statd
 4626 ?        00:00:00 hcid
 4631 ?        00:00:00 sh
 4632 ?        00:00:00 esd
 4635 ?        00:00:00 sdpd
 4645 ?        00:00:00 hidd
 4651 ?        00:00:00 krfcommd
 4664 ?        00:00:00 mdadm
 4699 ?        00:00:00 atd
 4715 ?        00:00:00 cron
 4808 ?        00:00:00 metacity
 4810 ?        00:00:01 gnome-panel
 4812 ?        00:00:01 nautilus
 4816 ?        00:00:00 bonobo-activati
 4827 ?        00:00:00 gnome-volume-ma
 4831 ?        00:00:00 update-notifier
 4833 ?        00:00:00 gnome-terminal
 4835 ?        00:00:00 evolution-alarm
 4839 ?        00:00:00 gnome-power-man
 4857 ?        00:00:00 gnome-pty-helpe
 4859 pts/0    00:00:00 bash
 4862 ?        00:00:00 evolution-data-
 4865 ?        00:00:00 trashapplet
 4883 ?        00:00:00 mapping-daemon
 4917 ?        00:00:00 mixer_applet2
 4918 ?        00:00:00 gnome-screensav
 4923 ?        00:00:06 firefox-bin
 4936 ?        00:00:00 netstat <defunct>
 5099 ?        00:00:00 cupsd
 5161 ?        00:00:00 pdflush
 5241 ?        00:00:00 syslogd
 5245 pts/0    00:00:00 dpkg
 5246 pts/0    00:00:00 update-manager.
 5271 pts/0    00:00:00 python2.4
 5279 pts/1    00:00:00 bash
 5287 pts/1    00:00:00 ps

---

### Post by rillip on 2007-04-01
Had to run my own to be sure, I think the updat-emanager and dpkg are conflicting here.

Worst case scenario, you should be able to close your session and start afresh without issue.

---

### Post by gc1 on 2007-04-29
I have the same problem as before and after a search on Forums I tried the aptitude clean command
The following result may give a clue for someone cleverer than I am:

gra@localhost:~$ sudo aptitude clean
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

NO OTHER PROCESS HAS BEEN STARTED BY ME but is there something starting automatcally due to a past error? Starting a new session has never cleared the problem.

---

### Post by vpsubramanian on 2008-06-09
Hi!

I got a similar message when I was doing apt-get install with --fix-missing. After trying others, I finally went to the base directory where the lock was and removed the lock file and retried apt-get. It seems to work fine.

---

