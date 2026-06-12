---
title: "glibc detected *** lockfile-create: free(): invalid next size (fast): 0x08525008 ***"
date: 2013-09-16
forum: Installation &amp; Upgrades
---

### Post by kinetonat on 2013-09-16
[B]glibc detected *** lockfile-create: free(): invalid next size (fast): 0x08525008 ***
*** glibc detected *** lockfile-create: malloc(): memory corruption (fast): 0x08525048 **[/B]*

I'm offered only a partial upgrade but then it cannot do that, up pops messages about the lock below, and it cannot proceed. In software centre, there is a searching in progress notification, which will not cancel down or complete, despite all attempts at rebooting etc. I have tried to remove ntp (which might be the problem software, and it will not start removing but will be listed as in progress and this does disappear if rebooted).

The story so far:

I tried this command in the terminal and thought it might be working as it began to many packages.sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update

suggested in thread [http://ubuntuforums.org/showthread.php?t=1986288](http://ubuntuforums.org/showthread.php?t=1986288)

However I get this further message:

Fetched 19.8 MB in 38s (520 kB/s)                                              
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

and tried again with apt get-update, which returned

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ap@ap-HP-Compaq-dc7600-Convertible-Minitower:~$ 

It seems to have been happening since i went in search of software in  the software centre (12.04 LTS), which could not be found, that the  searching just won't stop. I have tried to kill the software centre, log  out, and reboot but constantly the 'progress arrows' still show a  search continuing.

This is shown also in update manager: 'Unable to get exclusive lock. This usually means that another package management application (like  apt-get or aptitude) is already running. Please close that application  first.'

just tried this command:
sudo rm /var/lib/dpkg/lock

And now have something new going on - as pictured

it just hung there.

In terminal i can see the problem as:

Fetched 19.8 MB in 1min 48s (183 kB/s)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.        SO I TRIED THIS.......
****-HP-Compaq-dc7600-Convertible-Minitower:~$ sudo dpkg --configure -a

AND RETURNED THIS:

Setting up ntp (1:4.2.6.p3+dfsg-1ubuntu3.1) ...
 * Starting NTP server ntpd              [B]                                       *** glibc detected *** lockfile-create: free(): invalid next size (fast): 0x08525008 ***
*** glibc detected *** lockfile-create: malloc(): memory corruption (fast): 0x08525048 **[/B]*



I tried this command in the terminal and thought it might be working as   it began to many packages.sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update

suggested in thread [http://ubuntuforums.org/showthread.php?t=1986288](http://ubuntuforums.org/showthread.php?t=1986288)

However I get this further message:

Fetched 19.8 MB in 38s (520 kB/s)                                              
E: Could not get lock /var/lib/dpkg

edited: just tried again and returned:

dpkg: error: dpkg status database is locked by another process.



Now checking what systems are running -  can anyone see the problem one?:
 -Compaq-dc7600-Convertible-Minitower:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 kworker/u:0
    6 ?        00:00:00 migration/0
    7 ?        00:00:00 watchdog/0
    8 ?        00:00:00 migration/1

   10 ?        00:00:00 ksoftirqd/1
   12 ?        00:00:00 watchdog/1
   13 ?        00:00:00 cpuset
   14 ?        00:00:00 khelper
   15 ?        00:00:00 kdevtmpfs
   16 ?        00:00:00 netns
   18 ?        00:00:00 sync_supers
   19 ?        00:00:00 bdi-default
   20 ?        00:00:00 kintegrityd
   21 ?        00:00:00 kblockd
   22 ?        00:00:00 ata_sff
   23 ?        00:00:00 khubd
   24 ?        00:00:00 md
   26 ?        00:00:00 khungtaskd
   27 ?        00:00:04 kswapd0
   28 ?        00:00:00 ksmd
   29 ?        00:00:00 khugepaged
   30 ?        00:00:00 fsnotify_mark
   31 ?        00:00:00 ecryptfs-kthrea
   32 ?        00:00:00 crypto
   40 ?        00:00:00 kthrotld
   42 ?        00:00:00 scsi_eh_0
   43 ?        00:00:00 scsi_eh_1
   44 ?        00:00:00 scsi_eh_2
   45 ?        00:00:00 scsi_eh_3
   46 ?        00:00:00 kworker/u:3
   68 ?        00:00:00 devfreq_wq
  262 ?        00:00:02 jbd2/sdb1-8
  263 ?        00:00:00 ext4-dio-unwrit
  284 ?        00:00:00 ureadahead
  374 ?        00:00:01 flush-8:16
  480 ?        00:00:00 upstart-udev-br
  497 ?        00:00:00 udevd
  506 ?        00:00:02 rsyslogd
  513 ?        00:00:01 dbus-daemon
  615 ?        00:00:00 kpsmoused
  669 ?        00:00:00 udevd
  670 ?        00:00:00 udevd
  847 ?        00:00:00 bluetoothd
  869 ?        00:00:00 krfcommd
  920 ?        00:00:00 avahi-daemon
  921 ?        00:00:00 avahi-daemon
  935 ?        00:00:00 hci0
  940 ?        00:00:00 hd-audio0
  950 ?        00:00:00 hd-audio1
  975 ?        00:00:00 cupsd
 1019 ?        00:00:00 smbd
 1027 ?        00:00:00 upstart-socket-
 1070 ?        00:00:00 modem-manager
 1123 ?        00:00:00 colord
 1124 ?        00:00:00 NetworkManager
 1139 ?        00:00:00 polkitd
 1145 ?        00:00:00 smbd
 1189 ?        00:00:00 rc
 1192 tty4     00:00:00 getty
 1197 tty5     00:00:00 getty
 1202 ?        00:00:00 gdomap
 1207 tty2     00:00:00 getty
 1208 tty3     00:00:00 getty
 1210 tty6     00:00:00 getty
 1226 ?        00:00:00 acpid
 1228 ?        00:00:00 cron
 1229 ?        00:00:00 atd
 1242 ?        00:00:00 dhclient
 1249 ?        00:00:03 irqbalance
 1262 ?        00:00:00 lightdm
 1266 ?        00:00:00 whoopsie
 1292 tty7     00:35:04 Xorg
 1334 ?        00:00:00 dnsmasq
 1383 ?        00:00:00 master
 1430 ?        00:00:00 qmgr
 1438 ?        00:00:06 tor
 1452 ?        00:00:00 iprt
 1474 ?        00:00:00 ntpdate
 1482 ?        00:00:00 lockfile-create
 1549 ?        00:00:00 winbindd
 1560 ?        00:00:00 S23ntp
 1571 ?        00:00:00 lockfile-create
 1573 ?        00:00:00 winbindd
 1574 ?        00:00:00 nmbd
 1593 ?        00:00:00 accounts-daemon
 1610 ?        00:00:00 console-kit-dae
 1723 ?        00:00:00 upowerd
 1930 ?        00:00:00 rtkit-daemon
 1971 ?        00:00:00 lightdm
 2006 ?        00:00:00 gnome-keyring-d
 2017 ?        00:00:00 gnome-session
 2057 ?        00:00:00 ssh-agent
 2060 ?        00:00:00 dbus-launch
 2061 ?        00:00:17 dbus-daemon
 2065 ?        00:00:00 gvfsd
 2071 ?        00:00:00 gconfd-2
 2079 ?        00:00:13 gnome-settings-
 2085 ?        00:12:12 compiz
 2096 ?        00:05:21 pulseaudio
 2099 ?        00:00:00 gvfsd-metadata
 2102 ?        00:00:00 gconf-helper
 2110 ?        00:00:00 nm-applet
 2111 ?        00:00:00 bluetooth-apple
 2112 ?        00:00:29 nautilus
 2113 ?        00:00:00 polkit-gnome-au
 2128 ?        00:00:00 gnome-fallback-
 2136 ?        00:00:00 gvfs-gdu-volume
 2145 ?        00:00:03 udisks-daemon
 2146 ?        00:00:00 udisks-daemon
 2149 ?        00:00:00 gvfs-afc-volume
 2152 ?        00:00:00 gvfs-gphoto2-vo
 2158 ?        00:00:54 dropbox
 2161 ?        00:00:00 gdu-notificatio
 2167 ?        00:00:00 gvfsd-trash
 2175 ?        00:00:00 telepathy-indic
 2213 ?        00:00:17 bamfdaemon
 2217 ?        00:00:00 gvfsd-burn
 2219 ?        00:00:00 mission-control
 2224 ?        00:00:00 goa-daemon
 2230 ?        00:00:06 zeitgeist-datah
 2235 ?        00:00:00 gnome-screensav
 2241 ?        00:00:07 zeitgeist-daemo
 2274 ?        00:00:32 zeitgeist-fts
 2292 ?        00:00:00 evolution-alarm
 2311 ?        00:00:03 e-calendar-fact
 2316 ?        00:00:00 cat
 2319 ?        00:00:01 notify-osd
 2380 ?        00:00:24 unity-panel-ser
 2382 ?        00:00:11 hud-service
 2400 ?        00:00:00 indicator-sound
 2401 ?        00:00:00 indicator-messa
 2402 ?        00:00:00 indicator-sessi
 2404 ?        00:00:00 indicator-print
 2406 ?        00:00:01 indicator-appli
 2408 ?        00:00:02 indicator-datet
 2440 ?        00:00:00 geoclue-master
 2461 ?        00:00:00 ubuntu-geoip-pr
 2463 ?        00:00:00 e-addressbook-f
 2469 ?        00:00:01 glib-pacrunner
 2470 ?        00:00:00 sh
 2471 ?        00:00:14 gtk-window-deco
 2492 ?        00:00:47 ubuntuone-syncd
 2495 ?        00:00:01 update-notifier
 2567 ?        00:00:00 system-service-
 2592 ?        00:00:01 unity-files-dae
 2595 ?        00:00:03 unity-applicati
 2596 ?        00:00:01 unity-music-dae
 2597 ?        00:00:00 unity-lens-vide
 2637 ?        00:00:02 unity-scope-vid
 2641 ?        00:00:00 unity-musicstor
 2673 ?        00:00:00 aptd
 2679 pts/0    00:00:00 dpkg
 2689 pts/0    00:00:00 ntp.postinst
 2707 ?        00:00:00 deja-dup-monito
 2709 pts/0    00:00:00 invoke-rc.d
 2725 pts/0    00:00:00 ntp
 2730 pts/0    00:00:00 lockfile-create
 2735 ?        00:58:21 firefox
 2740 ?        00:10:58 chromium-browse
 2757 ?        00:00:07 chromium-browse
 2758 ?        00:00:00 chromium-browse
 2759 ?        00:00:00 chromium-browse
 2768 ?        00:00:00 chromium-browse
 2792 ?        00:00:00 at-spi-bus-laun
 2847 ?        00:00:44 chromium-browse
 2856 ?        00:04:35 chromium-browse
 2861 ?        00:00:19 chromium-browse
 2866 ?        00:00:03 chromium-browse
 2873 ?        00:00:04 chromium-browse
 2880 ?        00:00:00 chromium-browse
 2893 ?        00:02:40 chromium-browse
 2900 ?        00:09:19 chromium-browse
 2911 ?        00:00:03 chromium-browse
 2917 ?        00:00:01 chromium-browse
 2923 ?        00:00:00 chromium-browse
 2929 ?        00:00:22 chromium-browse
 2940 ?        00:00:27 chromium-browse
 2998 ?        00:02:40 chromium-browse
 3012 ?        00:54:13 chromium-browse
 3039 ?        00:00:00 chromium-browse
 3058 ?        00:53:11 chromium-browse
 3068 ?        00:00:08 chromium-browse
 3075 ?        00:00:27 chromium-browse
 3084 ?        00:00:00 chromium-browse
 3113 ?        00:00:12 chromium-browse
 3154 ?        00:00:01 chromium-browse
 3162 ?        00:00:17 chromium-browse
 3175 ?        00:00:05 chromium-browse
 3201 ?        00:00:02 chromium-browse
 3216 ?        00:00:18 chromium-browse
 3273 ?        00:00:03 chromium-browse
 3290 ?        00:00:00 chromium-browse
 3440 ?        00:00:00 dconf-service
 3458 ?        00:01:15 zoiper
 3607 ?        00:00:14 palimpsest
 3629 ?        00:00:00 jbd2/sdc1-8
 3630 ?        00:00:00 ext4-dio-unwrit
 3634 ?        00:00:00 jbd2/sdc5-8
 3635 ?        00:00:00 ext4-dio-unwrit
 3694 ?        00:39:02 plugin-containe
 4252 ?        00:00:00 gvfsd-computer
 4259 ?        00:00:00 gvfsd-network
 4276 ?        00:00:00 gvfsd-dnssd
 4286 ?        00:00:00 gvfsd-smb-brows
 5828 ?        00:00:00 oosplash
 5847 ?        00:00:25 soffice.bin
 6147 ?        00:00:00 pickup
 6194 ?        00:00:00 kworker/1:2
 6293 ?        00:00:00 kworker/0:0
 6347 ?        00:00:00 kworker/1:0
 6357 ?        00:00:00 kworker/0:1
 6374 ?        00:00:00 kworker/1:1
 6376 ?        00:00:31 software-center
 6411 ?        00:00:00 gvfsd-http
 6414 ?        00:00:00 kworker/0:2
 6453 ?        00:00:00 gnome-terminal
 6462 ?        00:00:00 gnome-pty-helpe
 6463 pts/2    00:00:00 bash
 6516 pts/2    00:00:00 ps

---

### Post by kinetonat on 2013-09-16
Using  sudo gnome-system-monitor

I killed the processes that 'looked ' ;)  troublesome!

lockfile-create x3 of those,
and 673 ?        00:00:00 aptd .....running at 200%

typed in sudo apt-get clean
sudo apt-get check

I looked to find updates were available, and have some downloaded and installed.
In Software Centre, the searching the had got stuck has been replaced with Applying Changes, which is progressing right now. I took advice from other sites I searched and found information on, that suggested trying to kill the process that got stuck. This thread was the most encouraging:
[URL="http://ubuntuforums.org/showthread.php?t=2054958"]http://ubuntuforums.org/showthread.php?t=2054958


update.
System updating successfully now on a day-to-day basis. No issue with Software Centre freeze-up.
[/URL]

---

### Post by kinetonat on 2013-12-11
Now attempting to upgrade........[h=2]distro upgrade probem 12.04lts to 12.10: glibc lockfile create free, and memory[/h] 		 				 					 					 				 				 		 			 				[INDENT] 					I have been running 12.04lts on a compaq dc7600 for a couple of  years. It seems over the past few months to have begun to hang. I'm  using both Chrome and Firefox, and FF often just fades to a shadow, and  hangs. Sometimes it will work ok for a few hours and then this starts,  and when it does it fades back into use for a few seconds...enough to  get it to respond and I can finish what i was doing. I tend to  force-quit the app and restart, usually a few times and then get a for  more hours before the problem comes back.

So, I decided to go for the upgrade of the distribution to 12.10.

I left it several hours to prepare the upgrade, set new software  channels, get new packages and now it has stopped at 'installed  python-libtorrent, with the following error [pictured]:

glibc detected   lockfile-create: free(): invalid next size (fast)
And,   glibc detected lockfile-create: malloc() memory corruption (fast)


I have looked at some other bugs reported but have not seen how to deal  with it eg that the host name might be too long...there was no solution  however, and at this stage in the upgrade I do not want to abort it...i  don't know how to safely anyway, when there may have been changes made  that will be unfinished. I am posting this from the same machine which  is still fully working as before - EXCEPT shockwave is not working so no  videos are playing or shown from the start. Hopefully someone can come  along and help rescue this, at least back to how it was in 12.04.

It was bust and i'm trying to fix it! :popcorn:

I've loads of applications and settings I wish to keep. I do not want a  fresh installation here. I am keeping the window open with the  distribution upgrade below 				



I NEARLY POSTED THIS...BUT IT IS THE SAME PROBLEM OVER AGAIN....how then to abort the upgrade succesfully, and then wait patiently I guess until next April for 14.0!
[/INDENT]

---

