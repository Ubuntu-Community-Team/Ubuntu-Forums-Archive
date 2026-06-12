---
title: "no deb"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by abbeychase on 2006-11-13
root@vera:/home/monni# deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper beryl-svn
bash: deb: command not found


this doesn't seem to be right...

---

### Post by aysiu on 2006-11-13
*deb* isn't a command.

What you've got there looks more like a line you want to add to your /etc/apt/sources.list.

```
sudo nano -B /etc/apt/sources.list
``` This will open your repositories list for editing. Add in this line at the end of the file: ```
deb http://3v1n0.tuxfamily.org dapper beryl-svn
``` Then save (Control-X, Y, Enter) and update ```
sudo aptitude update
``` Now you can install Beryl stuff from that repository.

Read more here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

