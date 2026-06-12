---
title: "Please Anybody Help Me How To Install Mysqlclient.a Library In Ubuntu"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by krisvamc on 2007-04-05
Hi,

****

Hi,

Could anybody please tell how to install **mysqlclient.a** library in **/usr/lib.**

[B]When I installed mysql client package from ubuntu, in /usr/lib it shows as libmysqlclient.a , but what I need is mysqlclient.a library.
[/B]

vamsi.

---

### Post by mssever on 2007-04-05
Why do you need to do this? If you installed mysql from Synaptic/aptitude/apt-get then something's probably messed up with your install. Try removing and reinstalling mysql.

If you used some other method of installing, you should remove it and use Synaptic/aptitude/apt-get unless you have a really good reason to do otherwise. This is because the package manager prevents a lot of problems.

If I've completely missed the point, please consider this a free bump! :-)

EDIT: I just re-read your post. You could try creating a symlink from /usr/lib/libmysqlclient.a to /usr/lib/mysqlclient.a

---

### Post by krisvamc on 2007-04-05
Hi,

I am installing MCC (Multicast Control client) software and for this I need some libraries. 

Mysqlclient.a is one of them.

I have installed mysql - client from sypnatic packet manager. 

Could you tell the procedure u were telling ? Should I have to type anything in the terminal.

Thanks for ur reply.

vamsi.

---

### Post by mssever on 2007-04-05
To make the symlink, open a terminal and do the following:
```
cd /usr/lib
sudo ln -s libmysqlclient.a mysqlclient.a
```

That should give you the necessary symlink. What I don't know is whether the lib you have is compatible. Try it and see.

---

### Post by krisvamc on 2007-04-05
The command you told changes libmysqlclient.a to mysqlclient.a? 

thanks for ur help.

vamsi.

---

### Post by mssever on 2007-04-05
> **krisvamc said:**
> The command you told changes libmysqlclient.a to mysqlclient.a? 

thanks for ur help.

vamsi.

It actually adds a link named mysqlclient.a that points to libmysqlclient.a.

---

