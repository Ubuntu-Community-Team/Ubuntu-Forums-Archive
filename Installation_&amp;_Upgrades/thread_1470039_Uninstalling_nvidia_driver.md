---
title: "Uninstalling nvidia driver"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by ankit singh on 2010-05-02
i installed nvidia195.36.24, now i want to delete all its traces and move to the default one, how should i do it?

---

### Post by ankit singh on 2010-05-02
i got it

---

### Post by Bobhuber on 2010-05-02
> **ankit singh said:**
> i installed nvidia195.36.24, now i want to delete all its traces and move to the default one, how should i do it?
Thats the driver you want (most recent) for the Nvidia vidio card for 2d/3d capability.

---

### Post by ankit singh on 2010-05-02
i have problems with lucid and i suspected nvidia for it, However looking in log i found that my system searches for /etc/gdm/custom.conf

[http://ubuntuforums.org/showthread.php?t=1468152](http://ubuntuforums.org/showthread.php?t=1468152)

system takes too much time to load after logging in.

also when i went to create custom.conf,
i had foll error

> ankit@ankit-desktop:~$ sudo gdmsetup

** (gdmsetup:2801): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:2801): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:2801): DEBUG: init delay=30
** (gdmsetup:2801): DEBUG: "/usr/share/xsessions/une-efl-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:2801): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:2801): DEBUG: "/usr/share/xsessions/une-guest-restricted.desktop" is hidden or contains non-executable TryExec program


** (gdmsetup:2801): WARNING **: Error calling GetValue('daemon/DefaultSession'): Key not found
** (gdmsetup:2801): DEBUG: Init default session found:'(null)'
** (gdmsetup:2801): DEBUG: Failed to identify the current session: Unable to lookup session information for process '2801'

** (gdmsetup:2801): WARNING **: Unable to find users: no seat-id found
** (gdmsetup:2801): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:2801): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:2801): DEBUG: adding monitor for '/home/ankit/.face'
** (gdmsetup:2801): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:2801): DEBUG: Found 1 sessions for user ankit
** (gdmsetup:2801): DEBUG: GdmUserManager: not adding session on other seat: /org/freedesktop/ConsoleKit/Session2

---

