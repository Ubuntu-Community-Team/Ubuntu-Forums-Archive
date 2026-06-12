---
title: "Fixed dbus / shopt problem"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by shousonhill on 2006-10-30
I had a couple of errors after upgrading to Edgy Eft

On logon I got the error "You logon lasted less than 10 seconds
/bashrc: 17: shopt: not found
/etc/bash_completion: 44: syntax error:  Bad substitution

Logged on under failsafe terminal and got another error:  unable to determine address of the message bus try man dbus-launch or dbus-daemon

I tried a bunch of things but I found that the root account had a line in its .bashrc file that my personal user lacked:
shopt -s checkwinsize

I just copied the root user's .bashrc over my personal user's /home/[username]/.bashrc and everything works (for now:) )

---

### Post by Co.Sinecure on 2007-04-10
Hmm...I'm getting the same message, although my .bashrc already has that line!

---

