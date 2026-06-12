---
title: "problem after reboot"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by mila80 on 2005-06-15
Hi all,
   I have a problem with ubuntu.
When I start my system, after having insert username and password, system get as output an error message:

"session during less of 10 seconds. If you don't make logout, is possibol that there are som installing problem or that there isn't free space on the Hard disk.  Use an emergence session to solve the problem"

details

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running /usr/bin/X11 sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "marco"
etc/gdm/Xsession/: Beginning session setup


I'm sorry for my English, but it is a translation.
Installing problem??? I installing ubuntu 4 mounth ago and I never had problem.


What can I do to solve the problem???

someone can help me???
Marco

---

### Post by Klin'Targ on 2005-06-15
This could be an issue writing to your home directory. Check to make sure you have write permission to your home directory and that the disk it resides on is not full.

---

### Post by mila80 on 2005-06-16
How can I do to know it???

---

### Post by jsuen on 2005-06-16
[QUOTE=mila80]How can I do to know it???[/QUOTE]
 bash$ ls -l /home/<your_account_name> ?
and
bash$ df
could be of use..

---

### Post by mila80 on 2005-06-16
Hi, I reply myself because I fix the problem...

sudo chown username:username /home/username/.ICEauthority

just do it...


Bye, Marco

---

