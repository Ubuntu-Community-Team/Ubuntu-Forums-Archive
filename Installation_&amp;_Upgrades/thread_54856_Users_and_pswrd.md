---
title: "Users and pswrd"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by hugoc on 2005-08-06
I have installed Ubuntu in my pc and i created a new user with his password, It functioned well, later i modified my own password (user-admin) and ocurrs an error, from this point I can't enter like user-admin and the other user created can't too. What I can do???

---

### Post by varunus on 2005-08-06
If you cannot log in at all:
Boot Ubuntu in recovery mode from the GRUB prompt.  Then, type "su yourusername" into the console that comes up.  Then, type "passwd" to set yourself a new password.  After that, type "exit".

If you can log in but just can't use sudo or change to admin user (sounds like your problem):
Boot into recovery mode as above, and type "visudo" into the prompt.  (This will launch VI; I'll help you with it in case you don't know how to use it).

Make sure the file looks like this:
```
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
%admin  ALL=(ALL) ALL
```

If it does, add the following line (it looks like your user got removed from the "admin" group):
```
yourusername ALL=(ALL) ALL
```
To add this line, press the insert key, then scroll around with the arrow keys, and type in the line exactly.  After you do this, press escape, then type SHIFT-SEMICOLON (colon, but you need to hold shift).  Then type "wq" and press enter.

Good luck, hopefully this fixes your problem.

---

### Post by hugoc on 2005-08-06
The problem was solved!!!. The second solution was OK. Thanks very much.

---

