---
title: "synaptic not working: lock problem"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by gc1 on 2007-05-26
Synaptic would not start but this error notice appeared:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
This was done, result as below...........

gra@localhost:~$ sudo dpkg --configure -a
Password:
Setting up linux-image-2.6.17-11-386 (2.6.17.1-11.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-11-386
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17.1-11.37 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17.1-11.37 was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.17-11-386
Found kernel: /vmlinuz-2.6.17-10-386
Found kernel: /vmlinuz-2.6.15-26-386
Found kernel: /vmlinuz-2.6.12-10-386
Found kernel: /vmlinuz-2.6.12-9-386
Found kernel: /vmlinuz-2.6.12-8-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up linux-libc-dev (2.6.17.1-11.38) ...
Setting up libsmbclient (3.0.22-1ubuntu4.2) ...
Setting up linux-headers-2.6.17-11 (2.6.17.1-11.38) ...

Setting up vim-runtime (7.0-035+1ubuntu5.1) ...
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

Then in Synaptic window I clicked on 'Reload' and the window showed all packages in the correct way.
Selecting installed (upgradeable) packages I found only the Firestarter package listed so I tried to upgrade this one. It downloaded files but upgrading stopped with this message:
E: Not locked
and
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

So I looked at what was running, using command ps -A

Result:
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
  100 ?        00:00:00 kseriod
  133 ?        00:00:00 pdflush
  135 ?        00:00:00 kswapd0
  136 ?        00:00:00 aio/0
 1671 ?        00:00:00 ata/0
 1736 ?        00:00:00 khubd
 1860 ?        00:00:00 kjournald
 1933 ?        00:00:00 logd
 2086 ?        00:00:00 udevd
 2829 ?        00:00:00 shpchpd
 2881 ?        00:00:00 kpsmoused
 2884 ?        00:00:00 kgameportd
 3209 ?        00:00:00 dhclient3
 3303 ?        00:00:00 kjournald
 3396 ?        00:00:00 portmap
 3575 tty1     00:00:00 getty
 3576 tty2     00:00:00 getty
 3577 tty3     00:00:00 getty
 3578 tty4     00:00:00 getty
 3579 tty5     00:00:00 getty
 3580 tty6     00:00:00 getty
 3772 ?        00:00:00 acpid
 3880 ?        00:00:00 dd
 3882 ?        00:00:00 klogd
 3901 ?        00:00:00 dbus-daemon
 3916 ?        00:00:01 hald
 3917 ?        00:00:00 hald-runner
 3923 ?        00:00:00 hald-addon-acpi
 3927 ?        00:00:00 hald-addon-keyb
 3956 ?        00:00:00 perl
 4031 ?        00:00:00 gdm
 4038 ?        00:00:00 gdm
 4041 tty7     00:02:25 Xorg
 4169 ?        00:00:00 freshclam
 4174 ?        00:00:00 x-session-manag
 4252 ?        00:00:00 ssh-agent
 4253 ?        00:00:00 ssh-agent
 4259 ?        00:00:00 dbus-launch
 4264 ?        00:00:00 dbus-daemon
 4288 ?        00:00:01 gconfd-2
 4414 ?        00:00:00 nfsd4
 4415 ?        00:00:00 nfsd
 4416 ?        00:00:00 nfsd
 4417 ?        00:00:00 nfsd
 4418 ?        00:00:00 nfsd
 4419 ?        00:00:00 lockd
 4420 ?        00:00:00 rpciod/0
 4421 ?        00:00:00 nfsd
 4422 ?        00:00:00 nfsd
 4423 ?        00:00:00 nfsd
 4424 ?        00:00:00 nfsd
 4428 ?        00:00:00 rpc.mountd
 4464 ?        00:00:00 gnome-keyring-d
 4467 ?        00:00:00 gnome-settings-
 4468 ?        00:00:00 nmbd
 4473 ?        00:00:00 smbd
 4526 ?        00:00:00 smbd
 4527 ?        00:00:00 rpc.statd
 4544 ?        00:00:00 hcid
 4550 ?        00:00:00 sdpd
 4558 ?        00:00:00 hidd
 4564 ?        00:00:00 krfcommd
 4577 ?        00:00:00 mdadm
 4615 ?        00:00:00 atd
 4628 ?        00:00:00 cron
 4652 ?        00:00:00 sh
 4653 ?        00:00:00 esd
 4729 ?        00:00:07 metacity
 4733 ?        00:00:04 gnome-panel
 4735 ?        00:00:02 nautilus
 4736 ?        00:00:00 gnome-volume-ma
 4740 ?        00:00:00 bonobo-activati
 4743 ?        00:00:00 update-notifier
 4754 ?        00:00:00 evolution-alarm
 4765 ?        00:00:00 gnome-power-man
 4776 ?        00:00:00 evolution-data-
 4778 ?        00:00:00 trashapplet
 4781 ?        00:00:00 mapping-daemon
 4819 ?        00:00:00 mixer_applet2
 4825 ?        00:00:01 gnome-screensav
 4834 ?        00:00:54 firefox-bin
 4871 ?        00:00:05 sol
 4970 ?        00:00:00 cupsd
 4977 ?        00:00:00 gs-esp
 4978 ?        00:00:02 rastertogutenpr
 4979 ?        00:00:00 usb
 5074 ?        00:00:00 syslogd
 5102 ?        00:00:14 gedit
 5173 ?        00:00:02 gnome-terminal
 5175 ?        00:00:00 gnome-pty-helpe
 5176 pts/0    00:00:00 bash
 5187 pts/0    00:00:00 dpkg
 5188 ?        00:00:00 pdflush
 8826 pts/0    00:00:00 update-manager.
 8851 pts/0    00:00:00 python2.4
 8945 pts/1    00:00:00 bash
 8953 pts/1    00:00:00 ps

I can't see a process running which could cause this "lock" problem

This is a permanent problem and I'd be very pleased to have some help......

---

### Post by Stephen Howard on 2007-05-26
its okay to delete the /var/lib/dpkg/lock file.  sometimes if one of the installation programs crashes (or is killed), it exits without deleting its lock file and the user has to manual do it instead.

A lock file is just an empty file that is created as a signpost to other applications that a database (in this instance the package database) is already in use.  When the installer finishes it just deletes the lock file.  So, go ahead and delete it.

---

### Post by rillip on 2007-05-26
This error is almost always caused by having Synaptic, apt, apt-get, add/remove programs, etc. running at the same time. I can't be 100% positive, but I don't think you can run dpkg at the same time as Synaptic.

---

### Post by gc1 on 2007-05-27
Thanks to both Stephen Howard and Rillip who gave hints that inspired me to battle on. I have had a lot of puzzling rubbish but got Synaptic to work in a funny way. This is the record of my latest attempt, installing gnome-games after I had uninstalled it as a test:

After a FRESH START of system
1  start Synaptic....E: dpkg was interrupted.....

2  ps -A showed at the end of a long list:
4728 ?        00:00:00 mixer_applet2
 4753 ?        00:00:00 gksudo
 4754 ?        00:00:00 synaptic
 4755 pts/1    00:00:00 ps

3  gra@localhost:~$ sudo dpkg --configure -a
Password:
Setting up update-manager (0.45.2) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 484 strings at 20 - 2848
Wrote aliases at 2848 - 29fc 4728 ?        00:00:00 mixer_applet2
 4753 ?        00:00:00 gksudo
 4754 ?        00:00:06 synaptic
 4805 ?        00:00:00 gnome-pty-helpe
 4806 pts/1    00:00:00 synaptic
 4831 pts/1    00:00:00 dpkg
 4832 pts/1    00:00:00 update-manager.
 4858 pts/1    00:00:00 python2.4
 4863 pts/0    00:00:00 ps

Wrote parents at 29fc - 33cc
Wrote literal globs at 33cc - 3430
Wrote suffix globs at 3430 - 68a8
Wrote full globs at 68a8 - 68cc 4728 ?        00:00:00 mixer_applet2
 4753 ?        00:00:00 gksudo
 4754 ?        00:00:06 synaptic
 4805 ?        00:00:00 gnome-pty-helpe
 4806 pts/1    00:00:00 synaptic
 4831 pts/1    00:00:00 dpkg
 4832 pts/1    00:00:00 update-manager.
 4858 pts/1    00:00:00 python2.4
 4863 pts/0    00:00:00 ps

Wrote magic at 68cc - bfb8
Wrote namespace list at bfb8 - bfc8
***
4  ps -A showed same as above

5  now clicked Synaptic's RELOAD button to get packages shown

6  tried to install package "gnome-games"...unsuccessful...details as below:

Selecting previously deselected package gnome-games.
(Reading database.....
Unpacking gnome games....
...

* Updating MIME database in /usr/share/mime. 4728 ?        00:00:00 mixer_applet2
 4753 ?        00:00:00 gksudo
 4754 ?        00:00:06 synaptic
 4805 ?        00:00:00 gnome-pty-helpe
 4806 pts/1    00:00:00 synaptic
 4831 pts/1    00:00:00 dpkg
 4832 pts/1    00:00:00 update-manager.
 4858 pts/1    00:00:00 python2.4
 4863 pts/0    00:00:00 ps
..
wrote 484 strings.....
....
& 8 similar lines
***
Installing hung there, preparing to configure gnome-games

7  ps -A now shows dpkg and update-manager are running as well as Synaptic:

 4728 ?        00:00:00 mixer_applet2
 4753 ?        00:00:00 gksudo
 4754 ?        00:00:06 synaptic
 4805 ?        00:00:00 gnome-pty-helpe
 4806 pts/1    00:00:00 synaptic
 4831 pts/1    00:00:00 dpkg
 4832 pts/1    00:00:00 update-manager.
 4858 pts/1    00:00:00 python2.4
 4863 pts/0    00:00:00 ps

8  HOWEVER the intallation of gnome games had finished successfully

9  Synaptic could not be closed normally because its menu was greyed out so I did a kill command to shut it down

10  QUESTION: did Synaptic hang because dpkg and update-manager had started up (without me asking for them)? I did not get any error message

---

