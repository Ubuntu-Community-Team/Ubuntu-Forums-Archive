---
title: "MySQL failed after upgrade to 9.10 desktop in 64bit"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by Oswy on 2010-04-11
I've just upgraded my 9.4 to 9.10 on my 64bit desktop PC. Shortly afterwards I noticed that MySQL had gone away. There was no mysqld running. I tried a restart to no effect. So tried an un-install and re-install with the Package Manager. This failed! 
There was quite an extensive message in details, which started:-

[I][FONT=Courier New]invoke-rc.d initscript mysql, action "start" failed
dpkg: error processing mysql-server-5.1 (--configure):
  subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent prevent configuration of mysql-server
[/FONT][/I]
And it goes on, but that's the essence of it. I subsequently tried a complete removal and re-install, to no avail.

I notice that /var/log/messages contains:

[I]Apr 12 01:10:15 Mintaka kernel: [ 2538.821153] type=1505 audit(1271031015.407:259): operation="profile_replace" pid=9328 name=/usr/sbin/mysqld
[/I]
Followed by many:

[I]Apr 12 01:10:15 Mintaka kernel: [ 2538.885370] type=1503 audit(1271031015.477:260): operation="open" pid=9355 parent=9354 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[/I]
Which looks as though it should mean something, but is meaningless to me.

Is there anyone who can shed light on the cause of the problem and how I might rectify it.
           Oswy

---

### Post by Oswy on 2010-04-13
This problem has now been resolved. It appears that the my.cnf file had been trashed during the upgrade. The doesn't seem to be any apparent cause, and the evidence has now been lost in the recovery process.

---

