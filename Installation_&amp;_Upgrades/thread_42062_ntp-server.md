---
title: "ntp-server"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by belred on 2005-06-15
i'm using kubuntu on virtual pc and and the time is about 50% slower than real time when running linux.  i run ntpupdate on boot and it sets the time correctly.  i then installed ntp-server and it can see during bootup that it starts successfully with OK.  i've also started and stopped the service manually and it appears to be working.  but it never changes the time.  i was told to let it run for a while, but after leaving it run over night, the time never got sync'd.  does ntp-server use the ntpupdate config file for it's servers?  any clue as to why ntp-server never sets the time?

thanks,

bryan

---

### Post by desdinova on 2005-06-15
What do you see in /var/log/syslog when you

sudo /etc/init.d/ntpdate restart?

---

### Post by belred on 2005-06-15
here's my session.  first i stoped and started ntp-server.  then i restarted ntpupdate as you suggested.  here's the logs for both.  after i did the ntpupdate restart command the clock DID sync correctly.  but not for ntp-server.  i thought that ntpupdate is a command you just one once peferably at boot before ntp-server.  then ntp-server would keep the time in sync from then on.

bryan@bryan2-ubuntu:~$ sudo /etc/init.d/ntp-server stop
 * Stopping NTP server...                                                [ ok ]
bryan@bryan2-ubuntu:~$ sudo /etc/init.d/ntp-server start
 * Starting NTP server...                                                [ ok ]
bryan@bryan2-ubuntu:~$ tail /var/log/syslog
Jun 15 18:18:51 localhost ntpd[5303]: ntpd exiting on signal 15
Jun 15 18:18:53 localhost ntpd[6130]: ntpd 4.2.0a@1:4.2.0a-11-r Mon Mar 14 12:39:28 GMT 2005 (1)
Jun 15 18:18:53 localhost ntpd[6130]: precision = 5.000 usec
Jun 15 18:18:53 localhost ntpd[6130]: Listening on interface wildcard, 0.0.0.0#123
Jun 15 18:18:53 localhost ntpd[6130]: Listening on interface wildcard, ::#123
Jun 15 18:18:53 localhost ntpd[6130]: Listening on interface lo, 127.0.0.1#123
Jun 15 18:18:53 localhost ntpd[6130]: Listening on interface eth0, 192.168.111.7#123
Jun 15 18:18:53 localhost ntpd[6130]: kernel time sync status 0040
Jun 15 18:18:53 localhost ntpd[6130]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Jun 15 18:19:12 localhost ntpd_initres[5430]: parent died before we finished, exiting
bryan@bryan2-ubuntu:~$


# TIME NOT SYNC'D


bryan@bryan2-ubuntu:~$ sudo /etc/init.d/ntpdate restart
 * Synchronizing clock to ntp.ubuntulinux.org...                         [ ok ]
bryan@bryan2-ubuntu:~$

# TIME SUCCESSFULLY SYNC'D


thanks,

bryan

---

### Post by desdinova on 2005-06-15
ntp-server turns your machine into a machine others can sync too

Here's my ntp.conf

# /etc/ntp.conf, configuration for ntpd

# ntpd will use syslog() if logfile is not defined
#logfile /var/log/ntpd

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
#server ntp.your-provider.example


# pool.ntp.org maps to more than 100 low-stratum NTP servers.
# Your server will pick a different set every time it starts up.
#  *** Please consider joining the pool! ***
#  ***  <http://www.pool.ntp.org/#join>  ***
#server pool.ntp.org

# ... and use the local system clock as a reference if all else fails
# NOTE: in a local network, set the local stratum of *one* stable server
# to 10; otherwise your clocks will drift apart if you lose connectivity.
fudge 127.127.1.0 stratum 13

# By default, exchange time with everybody, but don't allow configuration.
# See /usr/share/doc/ntp-doc/html/accopt.html for details.
restrict default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1 nomodify

# Clients from this (example!) subnet have unlimited access,
# but only if cryptographically authenticated
#restrict 192.168.123.0  mask  255.255.255.0 notrust

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet,
# de-comment the next lines. Please do this only if you trust everybody
# on the network!
#disable auth
#broadcastclient

server ntp2a.mcc.ac.uk
server ntp2b.mcc.ac.uk
server ntp.cs.strath.ac.uk


if the worst comes to the worst - put a command in /etc/crontab to restart ntpdate every 12 hours say

---

### Post by belred on 2005-06-15
i see, so ntp-server is for you to become a server.  i just uninstalled it and tried to add the following to kcron but it failed.

kdesu kcron
add under root/task: /etc/init.d/ntpdate restart
set silent, all hours and all 5-minutes
save and then i get this: "An error occured while updating crontab"

did i do something wrong?

bryan

---

### Post by desdinova on 2005-06-15
Just cron a command

ntpdate -s ntp.server.to.syncto

---

### Post by desdinova on 2005-06-15
my bad

ntpdate -u ntp.server.name

---

### Post by belred on 2005-06-15
sudo ntpdate -u ntp.ubuntulinux.org 

works on the command line.  but when i sudo kcron and add the command (without the sudo) in root/Tasks, it still fails when i save it with "An error occurred while updating crontab".

it looks like you can give multiple servers on the line so this should work great once i get it working it kcron.

sudo ntpdate -u ntp.ubuntulinux.org ntp.mycompany.net

thanks,

bryan

---

