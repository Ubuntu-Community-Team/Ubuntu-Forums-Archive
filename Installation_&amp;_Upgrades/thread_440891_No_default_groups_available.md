---
title: "No default groups available"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by gilkyboy on 2007-05-12
I recently installed Ubuntu, however, I had been struggling getting my sound to work.  Then, today I tried to use aplay as root and it worked.  I then tried it again as a normal user and it failed.  I then checked my groups and it turns out the only group I have is for my default user.    There's no audio group, no cd group, no groups at all really.  I'm wondering, is there a way to set these groups up properly without doing a lot of manual configuring and without destroying my system?  Thanks in advance for any help you guys can give, I really appreciate it.
    Gilkyboy

---

### Post by kidders on 2007-05-13
Hi there,

> **gilkyboy said:**
> I then checked my groups and it turns out the only group I have is for my default user. There's no audio group, no cd group, no groups at all really.That's *extremely* odd. Can I ask how you determined this? (Are you sure you're not confusing available groups with the ones you're a member of?)

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by gilkyboy on 2007-05-17
Yeah, I guess you were right there, but my default user wasn't a part of any groups.  That's kind of odd I thought.  However, I still don't have a lot of the default groups I don't think.  The ones I have are:
root, users, dhcp, syslog, klog, scanner, nvram, messageebus, ssl-cert, crontab, ssh, avahi-autoipd, avahi, netdev, lpadmin, haldaemon, powerdev, slocate, admin, gdm, fuse.  Should there be groups for things such as cd, audio, and things like that (or is my linux knowledge out of date :) ). 

What groups should my normal user be a part of?

Thanks for all your help,
    Gilkyboy

---

### Post by kidders on 2007-05-17
> **gilkyboy said:**
> Should there be groups for things such as cd, audio, and things like that (or is my linux knowledge out of date :) ).Things like that are very system-dependent. Here's a list from a pretty fresh Ubuntu install..

```
$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:kidders
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,kidders
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,kidders
floppy:x:25:haldaemon,kidders
tape:x:26:
sudo:x:27:
audio:x:29:kidders
dip:x:30:kidders
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:kidders
sasl:x:45:
plugdev:x:46:haldaemon,kidders
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
messagebus:x:104:
ssl-cert:x:105:cupsys
crontab:x:106:
ssh:x:107:
avahi-autoipd:x:108:
avahi:x:109:
netdev:x:110:kidders
lpadmin:x:111:kidders
haldaemon:x:112:
powerdev:x:113:haldaemon,kidders
scanner:x:114:cupsys,hplip,kidders
slocate:x:115:
admin:x:116:kidders
gdm:x:117:
fuse:x:118:
kidders:x:1000:
nvram:x:119:
ntp:x:120:
saned:x:121:
```If you seem to be missing things, adding them manually may be the wrong thing to do. Groups for managing access control to optical drives or sound cards may or may not be necessary, depending on how your system is configured ... so if you're system doesn't *need* a "cdrom" group, there may not be any point in having one.

> **gilkyboy said:**
> What groups should my normal user be a part of?That's a matter of personal preference really. Group membership tends to loosen the access restrictions a user is subject to, so I would really only add a user to a group if the specific need arose. As a simple example, you will always want (on a default Ubuntu system) to have at least one user in the "admin" group (ie to use **sudo**), so you don't ever have to use the root account. Whether to add any _more_ than one user to "admin" is up to you.


Again, just as an example, here are my current group memberships:

```
$ groups
kidders adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin
```Strictly, I could remove "floppy", "lpadmin", "dialout" & "scanner" without any ill effects, but I need the others to make full use of my computer.

---

