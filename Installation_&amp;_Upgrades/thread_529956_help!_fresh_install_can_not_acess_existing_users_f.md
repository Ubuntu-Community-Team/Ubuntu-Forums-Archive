---
title: "help! fresh install can not acess existing users from home folder"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by snkiz on 2007-08-19
I had to reinstall messed things up to much playing with my partitions. I had my home older on a separate partition so all the user data is still intact but when I try to log in any of the old users I get two errors.
The first one says the .dmc file is being ignored because of incorrect file permissions 
(Not a direct quote a quick search tells me that is a fairly common problem although I don't know how to fix it)

the second problem causes the session to crash and I get this error:

/etc/gdm/presession/default: registering your session with wtmp and utmp
/etc/gdm/presession/default: running: /usr/x11r6/bin/sessreg -a -w /var/log -u /var/run/utmp -x"/var/lib/gdm/:20_xservers" -h "-l ":20"  "snkiz"
/etc/gdm/xsesion: beginning session startup
could not set mode 0700 on private per-user gnome configuration directory '/home/sniz/.gnome2_private/': operation not permitted 

the posts I read before I re-installed didn't mention anything like this a little help please:confused:

---

### Post by kidders on 2007-08-20
Hi there,

You should make sure that your filesystem permissions are sensible, before trying to use X. Gnome/etc. can't function if they can't access their own settings properly.

---

### Post by Soarer on 2007-08-21
I had this when doing the same thing as you. In fact the error messages are quite informative.

Open a terminal, go to the directory you want to be home (/home/oldusername) and type
```

sudo chmod 644 .dmrc
```

Go up one (into /home) and type:

```
sudo chmod 755 oldusername
```

Gnome won't let you login unless the permissions are sensible (no writing by other users, or changing of .dmrc or .gnome2_private)

You may jsut need to change the owner of the directory & files. You could try:

```
sudo chown -R newusername /home/oldusername 
``` instead of the above if you haven't changed permissions onthe files by moving them around etc.

This will change the owner of that directory to your new user name. It may be that the newusername is the same as oldusername but Ubuntu regards them as different (different user number).

---

