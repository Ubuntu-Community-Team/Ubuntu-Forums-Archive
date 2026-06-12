---
title: "Can't sudo"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by kariudo@gmail.com on 2006-06-10
I just did a fresh install, and while trying to configure a few things couldn't figure out why most commands wouldn't run. Then the obvious became clear....I don't think I'm on the sudoers list for some odd reason. So I figured I would just switch to root and fix that....WRONG, no root password/access in Ubuntu by default. So here is where that brilliant idea fails in everyway...you need to sudo to enable root...cant sudo without root...sooo...WTF? 

So, to the relevant question, is there a way around this? Can I use some altered incarnation of a single user mode or something here, or am I pretty much just boned and have to reinstall and hope it doesnt dongle me again?

Any help appreciated. Cheers

--Kariudo

---

### Post by aysiu on 2006-06-10
Boot into *recovery mode*. You'll be root, and you can add yourself to the *admin* group in /etc/group.

```
cp /etc/group /etc/group_old
nano /etc/group
``` Your /etc/group file should look like this: ```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:kariudo
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:kariudo,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:kariudo,haldaemon
floppy:x:25:kariudo,haldaemon
tape:x:26:
sudo:x:27:
audio:x:29:kariudo
dip:x:30:kariudo
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:kariudo
sasl:x:45:
plugdev:x:46:kariudo,haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
kariudo:x:1000:
lpadmin:x:104:kariudo
scanner:x:105:kariudo,cupsys
**admin:x:106:kariudo**
crontab:x:107:
ssh:x:108:
messagebus:x:109:
haldaemon:x:110:
slocate:x:111:
``` Then ```
cp /etc/sudoers /etc/sudoers_old
nano /etc/sudoers
``` Make sure it looks like this: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
**%admin  ALL=(ALL) ALL**
``` The most important lines in both files are in **bold**.

---

### Post by kariudo@gmail.com on 2006-06-10
Groovy. Thanks.

---

### Post by gsaito on 2006-06-10
Thanks a lot aysiu!!!! I was having the same problem and solved doing this. I think there is a bug in the Alternate distribution CD of Ubuntu 6.06.... I made a fresh install twice and in both occasions the first created user did not have sudo permission.

---

### Post by aysiu on 2006-06-10
If you really do believe it to be a bug, click the link at the top-right of the forum page and file a bug report. That may fix it.

---

