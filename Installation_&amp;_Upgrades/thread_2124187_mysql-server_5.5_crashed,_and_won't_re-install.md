---
title: "mysql-server 5.5 crashed, and won't re-install"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by Darghon on 2013-03-10
Hi all,

I have a media server at home, with a mysql installed, My xbmc clients all connect to that server, and yesterday it suddenly crashed when I removed a video from my library.
Since then, I was no longer able to restart mysql with the notice that the startup job failed.

Looking at the logs, it seems that it starts, gets terminated with a status 1, and attempts to restart, until it complains that it restarted to much.

So, after some googling, I removed mysql from my system (commands I executed:)
```

apt-get remove --purge mysql-server mysql-client mysql-common
apt-get autoremove
apt-get autoclean

```

After which I searched the system for any mysql folders, and deleted them.

Next step, I attempted to reinstall mysql-server, and that "works" as it prompts me for a admin password, which I supply, it confirms, and then it complains that it was unable to set the password, and the install crashes.
I can trigger the prompt again by typing "dpkg --configure -a" but it always results in the same issue...

Can anyone help me resolve this, please... I've wasted to much time on this as it is.
And I've had this problem before (last week) and my solution then was a re-install of the complete system.
Lets say I don't want to do that again...

---

### Post by SeijiSensei on 2013-03-10
Did you run all these commands with "sudo" (e.g, "sudo apt-get ...").  You cannot do anything like installing or configuring mysql as an ordinary user.

---

### Post by Darghon on 2013-03-10
Yea, I switched to root, and then ran those commands (sudo -i)

---

### Post by steeldriver on 2013-03-10
Would you mind posting some of the log entries?

I'm not a mysql expert but a couple of issues I've come across in the past:

1. apparmor - in particular, there's been at least one /etc/apparmor.d/usr.sbin.mysqld update that shipped with syntax errors

2. iirc purge doesn't actually remove everything (for quite sensible reasons - you usually want to preserve any actual dbs and .cnf files) so an existing /etc/mysql/my.cnf or included files might still be messing things

3. if pkg reconfigure is unable to set the root password, maybe the mysql database itself got corrupted - in that case you may need to use --skip-grant-tables to get in and fix it

I presume you checked the obvious stuff like stale lock/pid files (although they should be in tmpfs I think)?

```

/run/mysqld/mysqld.pid
/run/mysqld/mysqld.sock

```

---

### Post by Darghon on 2013-03-10
1. Apparmor:
```

# vim:syntax=apparmor
# Last Modified: Tue Jun 19 17:37:30 2007
#include <tunables/global>


/usr/sbin/mysqld {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/mysql>
  #include <abstractions/winbind>


  capability dac_override,
  capability sys_resource,
  capability setgid,
  capability setuid,


  network tcp,


  /etc/hosts.allow r,
  /etc/hosts.deny r,


  /etc/mysql/*.pem r,
  /etc/mysql/conf.d/ r,
  /etc/mysql/conf.d/* r,
  /etc/mysql/*.cnf r,
  /usr/lib/mysql/plugin/ r,
  /usr/lib/mysql/plugin/*.so* mr,
  /usr/sbin/mysqld mr,
  /usr/share/mysql/** r,
  /var/log/mysql.log rw,
  /var/log/mysql.err rw,
  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
  /var/log/mysql/ r,
  /var/log/mysql/* rw,
  /var/run/mysqld/mysqld.pid w,
  /var/run/mysqld/mysqld.sock w,
  /run/mysqld/mysqld.pid w,
  /run/mysqld/mysqld.sock w,


  /sys/devices/system/cpu/ r,


  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.sbin.mysqld>
}

```

2. I deleted the following folders => /var/lib/mysql, /etc/mysql

3. I feel more of a MYSQL noob by the second, but here's what I get =>
```

root@sapprim:/var# mysqld --skip-grant-tables
130310 18:27:42 [ERROR] Can't find messagefile '/usr/share/mysql/errmsg.sys'

```

it seems I removed to much... in a attempt to completely remove mysql from the server (including /usr/share/mysql)

Both files named under the locks, do not exist on my system.

---

### Post by steeldriver on 2013-03-10
yes manually removing stuff can leave the package management broken

```
130310 18:27:42 [ERROR] Can't find messagefile '/usr/share/mysql/errmsg.sys'
```

probably just says that it can't tell you what the primary error is, because the message catalog is missing

That's about the limit of my experience of these things - however there are a couple of VERY knowledgeable mysql folks on the forum, I suggest you bump the thread on a weekday since they might be more active then

---

### Post by Darghon on 2013-03-21
Bump, this still isn't resolved...

---

