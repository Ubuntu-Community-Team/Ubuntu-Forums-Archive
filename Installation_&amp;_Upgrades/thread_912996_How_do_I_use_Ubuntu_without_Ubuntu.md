---
title: "How do I use Ubuntu without Ubuntu ?"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by ekh on 2008-09-07
Let me start saying I love using Ubuntu, I have used much time to install a collection of tools for embedded development on my Ubuntu workstation.

I have used Linux for more than 4 years and Ubuntu for more than 2 years on many machines...but

Recently my Ubuntu server got attacked (man in the middle attack), so I decided to use a portable only, until I could get on top of the situation again.

The portable got infected also, and also the 4 following reinstalls.
CD Checksum is OK.

This wasted a lot of time, so I shifted to OpenBSD. I have used it for a week now without getting infected. The Ubuntu last max. 4 hours before being infected.

As I don't want to skip my development workstation, I need a solution to get the repositories from the Ubuntu repository to my local Ubuntu server, so it can act as a mirror on the local net with no internet connection.

Getting the repositories to my local server can not include a solution where a Ubuntu machine gets internet connection. It is beyond my skills to avoid being infected with a clean default install.

So the only contact I have to the Internet is my OpenBSD machine.

I have searched the net for a usable solution without success. Any help to get a solution will be very welcome.

ekh

---

### Post by Pumalite on 2008-09-07
Can you clarify 'infected'. Did you identify the virus? Did you report it?

---

### Post by ekh on 2008-09-07
Thank you for a fast reply :-)

This thread provides many details:

[http://ubuntuforums.org/showthread.php?t=899529](http://ubuntuforums.org/showthread.php?t=899529) 

My last statement so far in the thread was:
"
Unless any from the Ubuntu community considers this important to follow up trying to improve the system, this is my final post in this thread.
"
I have not reported besides the thread above.

I used Ossec to detect the attacks the last times.

The "signature" of the attack was unexpected internet traffic. Loss of rights to write to usb key, changed binaries, changed file permissions,
slow response.

I have used more than a week trying to install a functional safe Ubuntu, but without success.

For my latest 5'th attempt I followed the advice here:

Hardening a Linux or OpenBSD Installation

[http://www.cromwell-intl.com/security/linux-hardening.html](http://www.cromwell-intl.com/security/linux-hardening.html)

Now the Ubuntu desktop is so "hardened" I can't access the net.

Edit:  I got the link wrong on Linux hardening. 
The rest of you not in trouble can apply one step at a time so you get more security. I fear the attack when removing the hardening adjustments.

---

### Post by ekh on 2008-09-07
Besides the security issue which goes beyond my skills, I will follow instructions to help investigation. But it will be no easy task.

My objective is also to get on with my daily work.

So please let me know if there is a way I can download the Ubuntu repositories with my OpenBSD machine, preferably to an usb harddisk.

Then move the harddisk to my ubuntu server and let this local server act as a mirror for itself and the other Ubuntu machines on the local net.

And the only computer ever connected to the internet is the OpenBSD machine.

---

### Post by _Fred_ on 2008-09-07
You are a strange guy ekh. If I didn't know any better I'd say you were putting these threads up for a laugh.

---

### Post by ekh on 2008-09-07
_Fred_, you are free to think what you want. I can assure you this is no laugh for me.

All I know is I have been developing embedded HW an SW for many years, first using Windows and then the last 6 months on Ubuntu with a self assembled tool collection.

One day my server root password does not work anymore, and the ssh connection I tried, informed me, that I probably had a man in the middle attack.

I had to use a live CD to get access to the server again.

Then my spare Ubuntu laptop started behaving strange.

My account to yahoo does not work anymore. I can not log in.
My account to ebay does not work anymore. I can not log in.

A long chat with ebay service and a new password checked during the chat did not succeed.

I have 4 Ubuntu reinstalls attacked to an unuseable state.
 
Now on the OpenBSD install I have been on the net for a week, but my previously lightning fast internet now works like a phone modem, and if I try using Tor I get no hole through anymore. A few days ago I could advance two pages before blocked.

My IP phone works as before.

_Fred_, you may think I'm a strange guy, I will admit this sounds very strange, especially when thinking back on two good years with no problems using Ubuntu for surfing and email, and 6 months for development also.

But please allow me to consider you _Fred_ a strange guy, not taking me seriously, and kicking a guy already lying down.

I have many computers and have done many installs, I have never seen this before.

This has a big impact on my ability to do my job. I am used having succes with what I do, and please don't consider my threads an escape from from following up on this. If somebody more skilled than me will instruct me, I will do my best to follow the instructions to get an insight into these strange attacs, if they continue, I have spare computers to employ in testing.

During my long professional working life I have worked with most facets of developing sw. I can't see how I can report this in a sensible way to Ubuntu developers, but please let me know if I'm wrong. I was hoping for some advice in the first place. 

Ekh

---

### Post by _Fred_ on 2008-09-07
If you are for real, I feel sorry for you. If you are having a laugh, you are doing a good job of it.

If you are for real, you should have kept your cracked ubuntu disk asside and done a fresh install and then done a few diff -rn dir dir commands after mounting both disks from a knoppix boot or similar.

You've told a great story, but you've posted little to nothing for anyone to help you with. That loses much/all of your credibility for you ;-)

If all else fails, get a distro that isn't as broken from trying to be nice to noobs as this one is. If you want security and stability, get debian stable or one of the more specialist security oriented distros.

I don't see a need to move to bsd, but it is always an option at the end of the day.

Fred. (without the _ and _ ;-) )

---

### Post by mikewhatever on 2008-09-07
> As I don't want to skip my development workstation, I need a solution to get the repositories from the Ubuntu repository to my local Ubuntu server, so it can act as a mirror on the local net with no internet connection.

Use whatever works best for you.
[Ubuntu Repositories]("http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=dw-distro")

---

### Post by collinp on 2008-09-07
If this guy is for real, which i extremely doubt, then with his "4 years of linux experience" he needs to fix his problem. There is no direct attack on Ubuntu machines without affecting the other linux machines in some way, it just cant happen.

---

### Post by _Fred_ on 2008-09-07
> **Hellow said:**
> There is no direct attack on Ubuntu machines without affecting the other linux machines in some way, it just cant happen.

As much as I agree with your sentiments, all the distros patch the kernels and tools to their own spec, so distro specific bugs do exist and specialised attacks could occur, BUT, still sounds like a crock of sh$t to me :-)

Fred.

---

### Post by collinp on 2008-09-07
> **_Fred_ said:**
> As much as I agree with your sentiments, all the distros patch the kernels and tools to their own spec, so distro specific bugs do exist and specialised attacks could occur, BUT, still sounds like a crock of sh$t to me :-)

Fred.

Well, it would seem to be extremely hard to single out one computer in a network unless you are on the network yourself and/or you know the private ip of the computer.

---

### Post by technotitclan on 2008-09-07
> **Hellow said:**
> Well, it would seem to be extremely hard to single out one computer in a network unless you are on the network yourself and/or you know the private ip of the computer.

i agree. you may want to ask you isp to change your ip address and then reinstall ubuntu-see if you have same problem

---

### Post by ekh on 2008-09-07
> **_Fred_ said:**
> As much as I agree with your sentiments, all the distros patch the kernels and tools to their own spec, so distro specific bugs do exist and specialised attacks could occur, BUT, still sounds like a crock of sh$t to me :-)

Fred.

OK, so you don't believe me, I don't think this is fair.

Take a look on [www.avrfreaks.net](www.avrfreaks.net), search the same name ekh. I have been there since 2001. I recently wrote a howto use Code::Blocks on my Ubuntu.

Peter Toft is a distinguished Linux person in Denmark, as well as Poul Henning Kamp (MD5), some of the Ubuntu members must know them. I am willing to present myself to one or both, so my story can be confirmed. 

Here I finally got a log file. it is the only log I have, but I guess the process can be repeated tomorrow, If someone is willing to direct my efforts, I will deliver all data here if I can get the log out. I have so far been able to get logs in the early stages of an attack.

To the latest comments:

Yes, I have thought of a new IP address too, but If I have to spend money for this, I must have a line with dhcp, or else it will only be a matter of time before my problems reappear.

```

  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (113 No route to host)
Err http://dk.archive.ubuntu.com hardy/universe Translation-en_DK              
  Could not connect to dk.archive.ubuntu.com:80 (130.226.1.35). - connect (113 No route to host)
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_DK     
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (113 No route to host)
Err http://dk.archive.ubuntu.com hardy/multiverse Translation-en_DK            
  Could not connect to dk.archive.ubuntu.com:80 (130.226.1.35). - connect (113 No route to host)
Ign http://security.ubuntu.com hardy-security Release                          
Err http://dk.archive.ubuntu.com hardy-updates Release.gpg                     
  Could not connect to dk.archive.ubuntu.com:80 (130.226.1.35). - connect (113 No route to host)
1% [Connecting to dk.archive.ubuntu.com (130.226.1.35)] [Connecting to security
ekh@t41fu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6232
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:25:2d:29:d2
Sending on   LPF/eth0/00:11:25:2d:29:d2
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.10.5 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:25:2d:29:d2
Sending on   LPF/eth0/00:11:25:2d:29:d2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPOFFER of 192.168.10.100 from 192.168.10.5
DHCPREQUEST of 192.168.10.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.10.100 from 192.168.10.5
bound to 192.168.10.100 -- renewal in 40269 seconds.
                                                                         [ OK ]
ekh@t41fu:~$ sudo tail -f -n300 /var/ossec/logs/alerts/2008/Aug/oo
tail: cannot open `/var/ossec/logs/alerts/2008/Aug/oo' for reading: No such file or directory
tail: no files remaining
ekh@t41fu:~$ sudo tail -f -n300 /var/ossec/logs/alerts/2008/Aug/ossec-alerts-30.log
** Alert 1220070976.0: mail  - ossec,
2008 Aug 30 06:36:16 t41fu->ossec-monitord
Rule: 502 (level 3) -> 'Ossec server started.'
Src IP: (none)
User: (none)
ossec: Ossec started.

** Alert 1220071192.179: mail  - ossec,
2008 Aug 30 06:39:52 t41fu->ossec-monitord
Rule: 502 (level 3) -> 'Ossec server started.'
Src IP: (none)
User: (none)
ossec: Ossec started.

** Alert 1220071237.360: mail  - syslog,errors,
2008 Aug 30 06:40:37 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 06:40:36 t41fu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

** Alert 1220071313.726: mail  - syslog,sudo
2008 Aug 30 06:41:53 t41fu->/var/log/auth.log
Rule: 5403 (level 4) -> 'First time user executed sudo.'
Src IP: (none)
User: ekh
Aug 30 06:41:51 t41fu sudo:      ekh : TTY=unknown ; PWD=/home/ekh ; USER=root ; COMMAND=/bin/echo got r00t?

** Alert 1220071313.1009: mail  - syslog,sudo
2008 Aug 30 06:41:53 t41fu->/var/log/auth.log
Rule: 5403 (level 4) -> 'First time user executed sudo.'
Src IP: (none)
User: (none)
Aug 30 06:41:51 t41fu sudo: pam_unix(sudo:session): session opened for user root by (uid=0)

** Alert 1220071313.1279: - syslog,sudo
2008 Aug 30 06:41:53 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:41:51 t41fu sudo:      ekh : TTY=unknown ; PWD=/home/ekh ; USER=root ; COMMAND=/usr/bin/nautilus --no-desktop file:///var/ossec

** Alert 1220071339.1588: - syslog,sudo
2008 Aug 30 06:42:19 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:42:17 t41fu sudo:      ekh : TTY=unknown ; PWD=/home/ekh ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 50331651 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpEVsvUz

** Alert 1220071381.2081: - syslog,sudo
2008 Aug 30 06:43:01 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:42:59 t41fu sudo:      ekh : TTY=unknown ; PWD=/home/ekh ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 50331651 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpPKVddf

** Alert 1220071439.2574: - syslog,sudo
2008 Aug 30 06:43:59 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:43:58 t41fu sudo:      ekh : TTY=pts/0 ; PWD=/home/ekh ; USER=root ; COMMAND=/usr/bin/apt-get update

** Alert 1220071483.2856: - syslog,sudo
2008 Aug 30 06:44:43 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:44:43 t41fu sudo:      ekh : TTY=pts/0 ; PWD=/home/ekh ; USER=root ; COMMAND=/etc/init.d/networking restart

** Alert 1220071513.3145: - syslog,sudo
2008 Aug 30 06:45:13 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:45:13 t41fu sudo:      ekh : TTY=unknown ; PWD=/home/ekh ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 50331651 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpfsGkGC

** Alert 1220071541.3638: - syslog,sudo
2008 Aug 30 06:45:41 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:45:40 t41fu sudo:      ekh : TTY=unknown ; PWD=/home/ekh ; USER=root ; COMMAND=/usr/bin/software-properties-gtk

** Alert 1220071629.3931: - syslog,sudo
2008 Aug 30 06:47:09 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:47:07 t41fu sudo:      ekh : TTY=unknown ; PWD=/home/ekh ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 50331651 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpAbr7T4

** Alert 1220071645.4424: - syslog,dpkg,
2008 Aug 30 06:47:25 t41fu->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2008-08-30 06:47:24 install libdns35 <none> 1:9.4.2-10ubuntu0.1

** Alert 1220071647.4678: mail  - syslog,dpkg,config_changed,
2008 Aug 30 06:47:27 t41fu->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2008-08-30 06:47:27 status installed libdns35 1:9.4.2-10ubuntu0.1

** Alert 1220071647.4944: mail  - syslog,dpkg,config_changed,
2008 Aug 30 06:47:27 t41fu->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2008-08-30 06:47:27 status installed libisccfg30 1:9.4.2-10ubuntu0.1

** Alert 1220071647.5213: mail  - syslog,dpkg,config_changed,
2008 Aug 30 06:47:27 t41fu->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2008-08-30 06:47:27 status installed libbind9-30 1:9.4.2-10ubuntu0.1

** Alert 1220071649.5482: mail  - syslog,dpkg,config_changed,
2008 Aug 30 06:47:29 t41fu->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2008-08-30 06:47:27 status installed bind9-host 1:9.4.2-10ubuntu0.1

** Alert 1220071649.5750: mail  - syslog,dpkg,config_changed,
2008 Aug 30 06:47:29 t41fu->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2008-08-30 06:47:27 status installed dnsutils 1:9.4.2-10ubuntu0.1

** Alert 1220071649.6016: mail  - syslog,dpkg,config_changed,
2008 Aug 30 06:47:29 t41fu->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2008-08-30 06:47:27 status installed libc6 2.7-10ubuntu3

** Alert 1220071763.6273: - syslog,sudo
2008 Aug 30 06:49:23 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:49:23 t41fu sudo:      ekh : TTY=pts/0 ; PWD=/home/ekh ; USER=root ; COMMAND=/usr/bin/tail -f -n300 /var/ossec/logs/alerts/2008/Aug/oo

** Alert 1220071795.6589: - syslog,sudo
2008 Aug 30 06:49:55 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:49:54 t41fu sudo:      ekh : TTY=pts/0 ; PWD=/home/ekh ; USER=root ; COMMAND=/usr/bin/tail -f -n300 /var/ossec/logs/alerts/2008/Aug/ossec-alerts-30.log

** Alert 1220071919.6922: mail  - ossec,rootcheck,
2008 Aug 30 06:51:59 t41fu->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/pulse-shm-479040509' present on /dev. Possible hidden file.

** Alert 1220072221.7188: - syslog,sudo
2008 Aug 30 06:57:01 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 06:57:00 t41fu sudo:      ekh : TTY=unknown ; PWD=/home/ekh ; USER=root ; COMMAND=/usr/sbin/synaptic

** Alert 1220072273.7467: - syslog,dpkg,
2008 Aug 30 06:57:53 t41fu->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2008-08-30 06:57:52 install thunderbird <none> 2.0.0.16+nobinonly-0ubuntu0.8.04.1

** Alert 1220072279.7739: mail  - syslog,dpkg,config_changed,
2008 Aug 30 06:57:59 t41fu->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2008-08-30 06:57:58 status installed thunderbird 2.0.0.16+nobinonly-0ubuntu0.8.04.1

** Alert 1220072279.8023: mail  - syslog,dpkg,config_changed,
2008 Aug 30 06:57:59 t41fu->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2008-08-30 06:57:58 status installed libc6 2.7-10ubuntu3

** Alert 1220072487.8280: mail  - syslog,errors,
2008 Aug 30 07:01:27 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 07:01:22 t41fu NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.NoReply - Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 

** Alert 1220072531.8796: mail  - syslog,errors,
2008 Aug 30 07:02:11 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 07:02:08 t41fu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Input/output error 

** Alert 1220072549.9133: mail  - syslog,errors,
2008 Aug 30 07:02:29 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 07:02:28 t41fu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Input/output error 

** Alert 1220072570.9470: mail  - syslog,errors,
2008 Aug 30 07:02:50 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 07:02:50 t41fu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Input/output error 

** Alert 1220072643.9807: mail  - syslog,errors,
2008 Aug 30 07:04:03 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 07:04:03 t41fu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Input/output error 

** Alert 1220072681.10144: mail  - syslog,errors,
2008 Aug 30 07:04:41 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 07:04:38 t41fu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Input/output error 

** Alert 1220074268.10482: mail  - syslog,errors,
2008 Aug 30 07:31:08 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 07:31:08 t41fu dhclient: receive_packet failed on eth0: Network is down

** Alert 1220074268.10751: mail  - syslog,errors,
2008 Aug 30 07:31:08 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 07:31:08 t41fu NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on eth1: No such device 

** Alert 1220092426.11074: mail  - syslog,errors,
2008 Aug 30 12:33:46 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 12:33:45 t41fu NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - hal-ipw-killswitch-linux returned 255 

** Alert 1220092442.11434: mail  - syslog,errors,
2008 Aug 30 12:34:02 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 12:34:01 t41fu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Input/output error 

** Alert 1220092442.11772: mail  - syslog,errors,
2008 Aug 30 12:34:02 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 12:34:01 t41fu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Input/output error 

** Alert 1220092444.12110: mail  - syslog,errors,
2008 Aug 30 12:34:04 t41fu->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 30 12:34:03 t41fu NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Input/output error 

** Alert 1220093174.12448: - syslog,sudo
2008 Aug 30 12:46:14 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 12:46:12 t41fu sudo:      ekh : TTY=unknown ; PWD=/var ; USER=root ; COMMAND=/bin/echo got r00t?

** Alert 1220093174.12724: - syslog,sudo
2008 Aug 30 12:46:14 t41fu->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: ekh
Aug 30 12:46:12 t41fu sudo:      ekh : TTY=unknown ; PWD=/var ; USER=root ; COMMAND=/usr/bin/nautilus --no-desktop file:///var

** Alert 1220093367.13023: mail  - ossec,
2008 Aug 30 12:49:27 t41fu->ossec-monitord
Rule: 502 (level 3) -> 'Ossec server started.'
Src IP: (none)
User: (none)
ossec: Ossec started.

** Alert 1220093574.13206: mail  - ossec,syscheck,
2008 Aug 30 12:52:54 t41fu->syscheck
Rule: 550 (level 7) -> 'Integrity checksum changed.'
Src IP: (none)
User: (none)
Integrity checksum changed for: '/etc/apt/sources.list'
Size changed from '3148' to '3167'
Old md5sum was: 'c1d70ae1a134069d789e801b87a3e527'
New md5sum is : '152858d7f5cfddd3b146a4bb24d747cf'
Old sha1sum was: 'b1383b2a8baed20600ddb821e91cebb30857c9a7'
New sha1sum is : '2ff842eeaa69e1f30c47d6aa04f24aced948c919'


** Alert 1220093590.13690: mail  - ossec,syscheck,
2008 Aug 30 12:53:10 t41fu->syscheck
Rule: 550 (level 7) -> 'Integrity checksum changed.'
Src IP: (none)
User: (none)
Integrity checksum changed for: '/etc/ld.so.cache'
Size changed from '44559' to '45843'
Old md5sum was: '42c9f3ea096f07179e3fbbc4284524f3'
New md5sum is : '3b40586c15782e6b4f8b4842192940c4'
Old sha1sum was: '8c6e3caed9a43b2a95238a117138eeecb48baf9d'
New sha1sum is : 'eb651e28b4bd6ed7386f9c0380130eec5b0b67a9'


** Alert 1220093859.14171: mail  - ossec,syscheck,
2008 Aug 30 12:57:39 t41fu->syscheck
Rule: 550 (level 7) -> 'Integrity checksum changed.'
Src IP: (none)
User: (none)
Integrity checksum changed for: '/usr/bin/nslookup'
Old md5sum was: '9e592dad0021d07782e64a797e82b3bc'
New md5sum is : '3d78aad140393a4142317f06b64eaa7d'
Old sha1sum was: '65cfb01ca9aadab67123db0b5137d3f568ac0f5d'
New sha1sum is : '72bfe7a9eae44dfb2b70de2edf2378f3e1678a92'


** Alert 1220093863.14616: mail  - ossec,syscheck,
2008 Aug 30 12:57:43 t41fu->syscheck
Rule: 550 (level 7) -> 'Integrity checksum changed.'
Src IP: (none)
User: (none)
Integrity checksum changed for: '/usr/bin/host'
Old md5sum was: '17717959e6f03f1801f5237cfffa5f86'
New md5sum is : '5978d78d573a236e0bcd84081b8294e2'
Old sha1sum was: '282caa0ef9cef90a34165d76ad9694a7a1abef19'
New sha1sum is : 'fe3469f3e0a6e9c65879c7cd515828a4442ca24c'


** Alert 1220093880.15057: mail  - ossec,syscheck,
2008 Aug 30 12:58:00 t41fu->syscheck
Rule: 550 (level 7) -> 'Integrity checksum changed.'
Src IP: (none)
User: (none)
Integrity checksum changed for: '/usr/bin/dig'
Size changed from '83980' to '84012'
Old md5sum was: '0e338901290b43d0a22205d2053439ee'
New md5sum is : '267c95dcff2849d30104de7800c79be8'
Old sha1sum was: '9fa42ae9f9041d54f54e007afdd0e5cc5412b84e'
New sha1sum is : '2ac3e39e35ee69df8ab92aee86dc03f9f1861fa0'


** Alert 1220093892.15534: mail  - ossec,syscheck,
2008 Aug 30 12:58:12 t41fu->syscheck
Rule: 550 (level 7) -> 'Integrity checksum changed.'
Src IP: (none)
User: (none)
Integrity checksum changed for: '/usr/bin/nsupdate'
Old md5sum was: '9a377c4bd792ba1ee8539626b9fe6502'
New md5sum is : 'e6c3e31c6ca34077799ae557715f1226'
Old sha1sum was: '2dbe0ab7303bdd111202f7a1c2ad64a47af0ed7b'
New sha1sum is : 'cc0969b694e5ec79789d6972e6b51194b6c2a4bc'


```

---

### Post by ekh on 2008-09-07
> **mikewhatever said:**
> Use whatever works best for you.
[Ubuntu Repositories]("http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=dw-distro")

Thank you for your answer. Your link states:

```

In a few easy steps, packages can be installed on any Ubuntu 8.04 based operating system, including Xubuntu, Edubuntu, Kubuntu, Ubuntu Studio, Ubuntu Ultimate, Mythbuntu, and Linux Mint.

Packages can be installed using APT, Synaptic Package Manager, or gdebi-gtk (for manual installation). Step-by-step instructions are provided.

```

I hoped someone could give a link to these instructions from another source.

I need to update eg. for new tools, and I can download the sources myself, when the raw download speed of 860kByte is in action. So buying a static snapshot is not a solution although it is a start, at least I get the instructions.

If you think, "Hey this guy says he used Linux for four years, why do he ask simple questions he ought to be able to solve himself". To those of you thinking this way, I can just say that I work aprox. 15 hours a day to get out of trouble. I'm used working long hours as I started a company 4 years ago also. 

Until recently I had a nice IT infrastructure and was able to focus on my work, now I only have my email and simple surfing, no trading, no netbank, almost no nothing :-(

You can be right I'm a strange guy, I often say you have to be a masochist to start a company in Denmark. Lots of work to do compared to an ordinary job.

---

### Post by nicol_bolas on 2008-09-07
1. Change ALL your passwords,
2. Change your boot order to only boot your hard drive and password protect your bios. you can always re-enable booting from a CD later.
3. Harden your kernel and use a good firewall.
4. Install ubuntu with the network cable unplugged.

Reasoning:
1. If you been hacked whoever is doing most likely has your passwords.
2. This will prevent a hacker from running a live CD remotely without the bios password.
3. Good sucurity measure.
4. Your system can be comprised during install, which might be your problem.

P.S. I hope that helps.

---

### Post by ekh on 2008-09-07
> **nicol_bolas said:**
> 1. Change ALL your passwords,
2. Change your boot order to only boot your hard drive and password protect your bios. you can always re-enable booting from a CD later.
3. Harden your kernel and use a good firewall.
4. Install ubuntu with the network cable unplugged.

Reasoning:
1. If you been hacked whoever is doing most likely has your passwords.
2. This will prevent a hacker from running a live CD remotely without the bios password.
3. Good sucurity measure.
4. Your system can be comprised during install, which might be your problem.

P.S. I hope that helps.

Thank you very much for helping.

> 1. Change ALL your passwords,"

Done for each install, looong paswords all classes.

> "2. Change your boot order to only boot your hard drive and password protect your bios. you can always re-enable booting from a CD later."

I was not aware of this possibility, I will fix this at next boot.
Question: Is it safe to update from the net after the first install when observing your advice ?

Im sitting on an old IBM thinkpad which has a button for changing the boot order outside the bios. I will check if I can disable completely.


> "3. Harden your kernel and use a good firewall."

The many attacks was on non-hardened installs of Ubuntu.

I then succesfully "hardened" by installing OpenBSD.

As my server was out of order, I used two Linksys WRT54GL in series with firewalls enabled. The firmware is now DD-WRT 1.24 SP1. previously just 1.24.

Lately I made a fresh install on two machines and followed the hardening instructions as descibed previously in this thread. But none can get on the internet now.

> 4. Install ubuntu with the network cable unplugged.
Done so.

---

### Post by PC-XT on 2008-09-08
I'm new to Ubuntu, but speaking networked computers generally, If you do a clean install and don't connect it to a network, it should be ok. If you did that for each computer before connecting them back together, it should get rid of the problem as long as it can't get back in from another source such as the Internet, a faulty device, external drive or removable disk. I usually also unplug all routers, switches, etc. during that time, if just to save a bit of unneeded electricity, but also to reset them since the new installs sometimes tend to work better that way. I would connect them one by one, with breaks in between to verify they work, making the connection to the OpenBSD computer last, after verifying the rest of the network works without attack. If there is an attack with no Internet or external program run to cause it, then the installation may be faulty. The exception I have heard to clean install not working is if the flashBIOS is the problem. Also, I suppose any firmware you replaced could perhaps be faulty also, but if you added things to the network one by one you could narrow the problem down to just what was connected when the attack occured. If the problem ever gets reintroduced, you can try to pinpoint how and avoid it.

---

### Post by ekh on 2008-09-08
> **PC-XT said:**
> I'm new to Ubuntu, but speaking networked computers generally, If you do a clean install and don't connect it to a network, it should be ok. If you did that for each computer before connecting them back together, it should get rid of the problem as long as it can't get back in from another source such as the Internet, a faulty device, external drive or removable disk. I usually also unplug all routers, switches, etc. during that time, if just to save a bit of unneeded electricity, but also to reset them since the new installs sometimes tend to work better that way. I would connect them one by one, with breaks in between to verify they work, making the connection to the OpenBSD computer last, after verifying the rest of the network works without attack. If there is an attack with no Internet or external program run to cause it, then the installation may be faulty. The exception I have heard to clean install not working is if the flashBIOS is the problem. Also, I suppose any firmware you replaced could perhaps be faulty also, but if you added things to the network one by one you could narrow the problem down to just what was connected when the attack occured. If the problem ever gets reintroduced, you can try to pinpoint how and avoid it.

Thank you very much for helping.

> I'm new to Ubuntu, but speaking networked computers generally, If you do a clean install and don't connect it to a network, it should be ok.

Without having done intensive testing, I have the same conclusion.

> If you did that for each computer before connecting them back together, it should get rid of the problem as long as it can't get back in from another source such as the Internet, a faulty device, external drive or removable disk.

I agree, so fa I have only operated one Ubuntu test PC connected to the internet or with the internet disconnected, to a media to transfer information. I am very focused to do this right.

To my best knowledge the install works perfectly until I connect to the internet to do an update. This does not exclude however, that something is inactive until an internet connection is established.

> Also, I suppose any firmware you replaced could perhaps be faulty also, but if you added things to the network one by one you could narrow the problem down to just what was connected when the attack occured. If the problem ever gets reintroduced, you can try to pinpoint how and avoid it.


I have studied the homepage of DD-WRT several days ago. They had a lengthy discussion approaching personal insult over some remaining IP addresses in the code. Some say it is a security risk, the maintainer claims it is of no importance, that the sources is corrected, and the correction will be out in the next release.

And some complains this possible vulnerability is not announced on the homepage.

I don't know what to believe, I guess the DD-WRT is the best I have. The original Linksys V1.1 firmware had a static DNS address I know for sure I did not add. And the extra address was not visible on the setup page, only on the status page.

---

### Post by ekh on 2008-09-08
I have just received 4 harddisks, this enables me to do more testing with less effort.

Having an initial install with some hardening added, I can clone the disk. It takes two hours (160GB), but it does not require actions from me, once initiated. If this ends up needing many tests, then I will try to get some 10GB disks, if possible.

I have two different machines both with a fresh initial install of Ubuntu desktop 8.04.1.

I then added the hardening advice on this page:

[http://www.cromwell-intl.com/security/linux-hardening.html](http://www.cromwell-intl.com/security/linux-hardening.html)

The specific modifications I did is listed below. Unfortunately it worked so well, that the machines cannot resolve DNS.

So eg.

```

ping www.dr.dk

```
gives no answer with an IP address

Pinging my router works.

If I remove all the hardening I consider the result given, with 5 previous attacks in memory. 

As this is some time consuming tests. I will be thankful, if I can get advice on one ore more hardening changes making internet connection impossible, so please check the list below as this possibly eventually can lead to a more secure Ubuntu. 

You do the suggestions, I do the testing.


```

Hardening list.

Kernel

sudo sysctl -w net.ipv4.icmp_echo_ignore_broadcasts=1

sudo sysctl -w net.ipv4.conf.all.accept_redirects=0
sudo sysctl -w net.ipv6.conf.all.accept_redirects=0

sudo sysctl net.ipv4.conf.all.send_redirects=0
##sudo sysctl net.ipv6.conf.all.send_redirects=0  # unknown in ubuntu

sudo sysctl net.ipv4.conf.all.accept_source_route=0
sudo sysctl net.ipv4.conf.all.forwarding=0

## sudo sysctl net.ipv4.conf.all.mc_forwarding=0  ## root has no permission to change this

sysctl -w net.ipv4.conf.all.rp_filter=1
sysctl -w net.ipv4.conf.all.log_martians=1

sysctl -w net.ipv4.tcp_max_syn_backlog=1280
sysctl -w net.ipv4.tcp_syncookies=1

Other stuff:

edit /etc/passwd file and disable all unneeded accounts, remember a backup aof the passwd file
After edit the only allowed account is my user account.

disable the avahi daemon by:
System > Administration > Services, untick "Multicast DNS service discovery"

In /etc/ssh/ssh_config

    Ciphers blowfish-cbc,aes256-cbc,aes256-ctr
    PasswordAuthentication no 
    PermitRootLogin no
    Protocol 2

Add a grub password
I have not done this.


```

---

### Post by Chayak on 2008-09-08
I've read the previous thread and I admit that I find it very hard to believe that any intelligence entity would care that you're part of a yahoo group on alternative energy with links to quack inventions.  In the scheme of things you are *not* that important.  Why would they bother expending the man hours of highly trained individuals who cost a lot to train and equip, much less field when the cost of security is factored in to watch someone on a *public* yahoo group on alternative energy?  In case you haven't thought about it these "spies" that hound you could just read your posts as well.  If it's on a government radar then they are already monitoring you at the ISP level and know what you're doing anyway.

That aside...

If you're really under the microscope then you're pretty much done for.  You could disconnect important machines from the internet but then they still have [TEMPEST]("http://en.wikipedia.org/wiki/TEMPEST") to record your long passwords from a distance.  I've seen hobby tempest devices from time to time that were scary, think what **they** have.  Then there is [this]("http://http://www.blackhat.com/presentations/bh-usa-08/Filiol/BH_USA_08_Filiol.zip") briefing that was given at Black Hat 2008 on getting data from non-networked computers both actively and passively.

What can you do?  Well there are defense measures against TEMPEST which involves turning the room your computers are in into a [faraday cage]("http://en.wikipedia.org/wiki/Faraday_Cage") which basically involves putting a conductive wire mesh around the room to contain RF emissions.  You also need to switch to shielded network cable to prevent RF leakage and possible injections remotely into your network.  Lan cables can interfere with each other, true? If they can then it's theoretically possible that a directed RF signal could inject data onto that unshielded line the same way antennas act for radios.  The longest passwords in the world are not going to help if they are sniffing your keystrokes remotely by the radio emissions coming from your keyboard cable.

Keep your clean network off the internet in a shielded room, use one hardened computer for internet access and when you need to send data burn a CD-R from your clean network and then send it with the hardened machine.  Do not under any circumstance take data from that hardened machine into your clean network as it could include hidden code to monitor and then hide data onto further media burned from that network that will be sent when it is put into an internet connected machine.  

Is it certain? no, but it's theoretically possible.  Then again the whole situation you claim to be in is just as sketchy in my mind as even PhDs can have paraniod delusions.  If they're really watching you then this should help though at the same time I did just put myself at risk by offering countermeasures.

Oh and as for your two routers/firewalls inline you might want to invest in a different firewall for the first or second layer as if they have an exploit to get through one of your current routers then the same exploit will get them through the second if they're the same.  You also might want to consider putting in a SNORT sensor between those two firewalls to catch any odd traffic.

---

### Post by ekh on 2008-09-08
> **Chayak said:**
> I've read the previous thread and I admit that I find it very hard to believe that any intelligence entity would care that you're part of a yahoo group on alternative energy with links to quack inventions.  In the scheme of things you are *not* that important. 

I agree with you, I am only a solitary experimenter, I am not going to mass produce anything related to the forbidden technology. 

I did a big mistake to publish some unusual experiments on a small forum. 3 days later the experiments were published (not by me) in a document on an Australian online university. Two days later my trouble began.

Thanks for the insightful advice.

As I mentioned previously I'm not here to convince anyone, It was just a detail among other details.

As I also told previously. I'm no internet/kernel expert, that's why I ask for help.

The question is if someone wants to help, so I can start working again, I have to do a living, and I have not been able to work for two weeks.

Please observe that the vulnerability in my machines also is in yours...

If I'm a nuissance to the forum, please let me know, and I will bother you no more.

---

### Post by _Fred_ on 2008-09-11
> **Chayak said:**
> I've read the previous thread and I admit that I find it very hard to believe that any intelligence entity would care that you're part of a yahoo group on alternative energy with links to quack inventions.  In the scheme of things you are *not* that important.  Why would they bother expending the man hours of highly trained individuals who cost a lot to train and equip, much less field when the cost of security is factored in to watch someone on a *public* yahoo group on alternative energy?

An excellent point. I'd just have you killed. It's fairly cheap and easy to have done at the end of the day...

---

### Post by marli2 on 2008-09-11
yeah but getting sombody killed dosent happen overnight.
however sound like an ameter.
I woulnt trust your router, in fact just thinking about it writing compromised firmware would be hugely advantage, once you are inside sombodys network, you are always inside tiher network, its the ultimate zombie. people FFR thier pcs all the time, very few flash thier firmware.(and even then ONLy when its out of date)negates NATs, negats HW firewall, always on, knows what machines are on your network, controls DNS and all IP traffic.

simple solution, pop over to a mates to do the install/update.

---

### Post by _Fred_ on 2008-09-11
> **marli2 said:**
> yeah but getting sombody killed dosent happen overnight.

Oh come ON! This is a big scary oil company/us gov conspiracy theory, anything can happen instantly ;-)

---

### Post by Rocket2DMn on 2008-09-11
Please keep this thread on topic or it will be closed.  It has already run its course...
That type of discussion is best left for the OPP forum.

---

### Post by ekh on 2008-09-13
To some posters in this thread I can just say, that persons behaving in a non-ethical way tell more about themselves, than the person they want to abuse.

It actually says a lot about the Ubuntu forum, that after a few not so nice posts, the moderator stops it [ thumbs up :-) ]. 

Nelson Mandelas life and definition of ubuntu is worth remembering.

I have found a very nice special edition of Ubuntu.

[www.polippix.org](www.polippix.org)

It is a live CD running in ram only, You can mount an USB stick to save downloaded stuff.

The best part: If you get infected, you just reboot, and the reboot is reasonable quick.

---

