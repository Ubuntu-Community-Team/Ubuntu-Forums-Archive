---
title: "change to localtime"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by b4nsh33 on 2007-11-22
hi, my ubuntu server installation changes my localtime to utc every time i reboot, i have installed ntp , this is my /etc/ntp.conf

# /etc/ntp.conf, configuration for ntpd

driftfile /var/lib/ntp/ntp.drift

# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server pool.ntp.org
#server ntp.ubuntu.com

# By default, exchange time with everybody, but don't allow configuration.
# See /usr/share/doc/ntp-doc/html/accopt.html for details.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

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

the command date always return utc time, ok, i adjunst it to utc-6, but the damm thing changes again to utc afeter every reboot, what do i do to make this change permanent?

---

