---
title: "No Login Screen After 8.04 Upgrade"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Gotit on 2008-05-01
I can't get a log in screen since upgrading to 8.04 via the update manager.

If it's of any help in troubleshooting for anyone to figure out why I can't get a login screen here's what my logs show (sorry for the length):

/var/log/syslog
```
May  1 18:18:39 Home-Ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  1 18:18:39 Home-Ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  1 18:18:39 Home-Ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: Withdrawing address record for 192.168.57.104 on eth0.
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.57.104.
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: Interface eth0.IPv4 no longer relevant for mDNS.
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.57.104.
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: New relevant interface eth0.IPv4 for mDNS.
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: Registering new address record for 192.168.57.104 on eth0.IPv4.
May  1 18:18:39 Home-Ubuntu NetworkManager: <info>  Old device 'eth0' activating, won't change. 
May  1 18:18:40 Home-Ubuntu NetworkManager: <info>  Clearing nscd hosts cache. 
May  1 18:18:40 Home-Ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May  1 18:18:40 Home-Ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  1 18:18:40 Home-Ubuntu NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
May  1 18:18:40 Home-Ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  1 18:18:40 Home-Ubuntu kernel: [  315.348206] NET: Registered protocol family 10
May  1 18:18:40 Home-Ubuntu kernel: [  315.348432] lo: Disabled Privacy Extensions
May  1 18:18:40 Home-Ubuntu kernel: [  315.349927] ADDRCONF(NETDEV_UP): wlan1: link is not ready
May  1 18:18:40 Home-Ubuntu gdm[5628]: WARNING: Couldn't authenticate user 
May  1 18:18:40 Home-Ubuntu ntpdate[6527]: adjust time server 91.189.94.4 offset 0.078495 sec
May  1 18:18:42 Home-Ubuntu avahi-daemon[5697]: Registering new address record for fe80::216:17ff:fe1e:49a0 on eth0.*.
May  1 18:18:42 Home-Ubuntu gdm[5628]: WARNING: Couldn't authenticate user 
May  1 18:18:50 Home-Ubuntu last message repeated 5 times
May  1 18:18:51 Home-Ubuntu kernel: [  326.204408] eth0: no IPv6 routers present
May  1 18:18:52 Home-Ubuntu gdm[5628]: WARNING: Couldn't authenticate user 
May  1 18:19:23 Home-Ubuntu last message repeated 18 times
May  1 18:19:27 Home-Ubuntu last message repeated 2 times
May  1 18:19:27 Home-Ubuntu init: tty4 main process (5016) killed by TERM signal
May  1 18:19:27 Home-Ubuntu init: tty5 main process (5017) killed by TERM signal
May  1 18:19:27 Home-Ubuntu init: tty2 main process (5021) killed by TERM signal
May  1 18:19:27 Home-Ubuntu init: tty3 main process (5022) killed by TERM signal
May  1 18:19:27 Home-Ubuntu init: tty6 main process (5023) killed by TERM signal
May  1 18:19:27 Home-Ubuntu init: tty1 main process (6339) killed by TERM signal
May  1 18:19:27 Home-Ubuntu avahi-daemon[5697]: Got SIGTERM, quitting.
May  1 18:19:27 Home-Ubuntu avahi-daemon[5697]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.57.104.
May  1 18:19:29 Home-Ubuntu kernel: [  364.410301] ip6_tables: (C) 2000-2006 Netfilter Core Team
May  1 18:19:30 Home-Ubuntu exiting on signal 15
```
Everything seems OK until I get the "gdm WARNING: Couldn't authenticate user"

So then I went to check my gdm log at /var/log/gdm/:0.log
```
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux Home-Ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  1 18:18:29 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "i2c" already built-in
(II) Module "ddc" already built-in
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
```

I didn't think this is too bad?  So I went off to check my authentication log because syslog reported an auth error.  Here's what I show in /var/log/auth.log
```
May  1 18:18:35 Home-Ubuntu gdm[5628]: pam_nologin(gdm:auth): cannot determine username
May  1 18:19:03 Home-Ubuntu last message repeated 17 times
May  1 18:19:05 Home-Ubuntu login[5022]: pam_unix(login:session): session opened for user steve by LOGIN(uid=0)
May  1 18:19:05 Home-Ubuntu gdm[5628]: pam_nologin(gdm:auth): cannot determine username
May  1 18:19:26 Home-Ubuntu last message repeated 12 times
May  1 18:19:27 Home-Ubuntu sudo:    steve : TTY=tty3 ; PWD=/home/steve ; USER=root ; COMMAND=/sbin/reboot
May  1 18:19:27 Home-Ubuntu sudo: pam_unix(sudo:session): session opened for user root by steve(uid=0)
May  1 18:19:27 Home-Ubuntu sudo: pam_unix(sudo:session): session closed for user root 
```
Ah ha! I thought, it's PAM causing my problems so I checked /etc/pam.d/gdm
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
```
And I think that looks OK and so does /etc/pam.d/gdm-autologin
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    required        pam_permit.so
@include common-account
session required        pam_limits.so
@include common-session
@include common-password
```

Thanks

---

### Post by kewan on 2008-07-09
Hi,

I have the same problem since upgrading to 8.04 and my logs look the same as yours.

Did you have any luck with fixing this?

Has me stumped...

---

### Post by lelandw on 2008-08-13
Same for me.  Any response from someone who got past this would be helpful, thanks.

---

### Post by ggrune on 2008-10-23
hi,

i have got the same problem after upgrading to 8.04.
Some lines before the final "* running final boot scripts ..." i have found an error like this "/etc/event.d/tty3:13: Unknown stanza"

My /etc/event.d/tty* scripts were broken. They looked like this
```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on runlevel-2
start on runlevel-3
start on runlevel-4
start on runlevel-5

stop on shutdown

respawn /sbin/getty 38400 tty1

```

now they look like this 
```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1

```

if someone needs the other five tty scripts i can post it. Just ask.
I hope it helps.

---

