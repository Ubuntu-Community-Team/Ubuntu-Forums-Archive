---
title: "mysqld_safe taking 100% CPU following automatic update today"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by akadruid on 2007-04-05
Hi all,

I ran the automatic update from the tray icon today (which included an update to MySQL), and since then the mysqld_safe process is taking every bit of available CPU.  MySQL is not in use at all.

Is there something I can do to stop this?  Or is there some way of rolling back the update?

Thanks

akaDruid

---

### Post by sn0w on 2007-04-07
I was having the same problem but I forcefully restarted it and it doesn't seem to be causing any more problems.

---

### Post by disk11 on 2007-04-07
I noticed this too.  Restarting /init.d/mysql didn't help, I had to kill mysql_safe in top, and it didn't come up when I restarted mysql.  I hope I didn't break anything.

---

### Post by tbfnews on 2007-10-12
I too have had this problem.  I needed to kill it twice.  And it doesn not seem to be a problem after a reboot.

---

### Post by DannyColligan on 2007-11-27
Same problem here on Gusty.  Tried killing the process and, rather comically, it just started back up again.  Rebooting my machine, as an above poster suggested, worked for me, although it makes me feel like such a Windows user.  Bleh.

---

### Post by michelev on 2007-12-02
Same problemi for me. "Kill" command on top dont works.

> xxxxxxx@ubuntu-xxxxxxxx:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

What's mean "not cleanly closed and upgrade needing tables?"

Any suggestion? Thanks to all
michelev

---

### Post by eeried on 2008-01-04
```
xxxxxxx@ubuntu-xxxxxxxx:~$ sudo /etc/init.d/mysql restart
* Stopping MySQL database server mysqld [ OK ]
* Starting MySQL database server mysqld [ OK ]
* Checking for corrupt, not cleanly closed and upgrade needing tables.
```

It's okay, mysql checks as it says, it doesn't say there's a problem.

Mysqld_safe looks like a bug, ti doesn't seem necessary for LAMP. 

I too had to kill it twice.

See : [http://ubuntuforums.org/showthread.php?p=4070088#post4070088](http://ubuntuforums.org/showthread.php?p=4070088#post4070088)

---

