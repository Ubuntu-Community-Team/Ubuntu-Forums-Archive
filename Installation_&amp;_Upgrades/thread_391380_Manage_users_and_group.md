---
title: "Manage users and group"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by giuseppe.dem on 2007-03-23
I have a simple and maybe very elementary question.
After installing ubuntu(edgy), I change my group properties, i.e. I am not any longer in
the admin group. I had to this because of many problems with skype and graphical applications lanched as root.
But now, when  I login, in the System->Administration menu I lost all previous 
application, e.g. Network Setup, User&Groups and so on.
So, I cannot use administration application under a user which is not in admin group?
This is not what I remember in Gnome or KDE.

Any reply is appreciated
Giusepp

---

### Post by bapoumba on 2007-03-23
Hello :)
In order to perform administrative tasks (ie the one that require sudo, or a root password) you have to be in the admin group.
Boot up in recovey mode from grub menu (you'll be root), login and give your password, and enter:
```
adduser <your_login_here> admin
reboot
```
You should be fine.

---

### Post by giuseppe.dem on 2007-03-23
Thanks for the reply.
I will be more detailed.
Before, when I was in the admin group, I had in System->Admin menu
all administrative tasks. Now, Ihave not. In fedora, you can have all kind
of menu (included administrative ones) and enter the password whenever 
it's needed. Is it a difference between fedora and ubuntu, or between kde and gnome?
Regards
:)

---

### Post by giuseppe.dem on 2007-03-24
Moreover, 
I would use synaptic even if I am not a user without admin privileges.
Why I cannot use use a fedora-style way? That is,
run synaptic and let the system ask me the root passowrd...
In ubuntu-gnome a can run synaptic, but the install process is separeted by the downloading process, which is very annoying...
Giuseppe

---

