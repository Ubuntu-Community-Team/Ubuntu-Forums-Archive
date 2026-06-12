---
title: "Root Password???"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Lvcoyote on 2007-12-02
just installed 7.10 Ubuntu and I was never asked to setup a root (super user) password???  Do I need one??  What did I do wrong??  I'm trying to edit some folders and it wont let me saying I dont have permission.  I logged off and tried to log back on as root, but I dont have a password...... I'm real confused here......LOL

---

### Post by bwald on 2007-12-02
Ubuntu assigns the root user a random password.  You should use "sudo" to run any root commands you want.  By default, the user account is in the sudoers group so you can run any root command.  If you really want to change the root user's password, run

```
sudo su
```

and then type whatever you want for the root password.

---

### Post by ruibernardo on 2007-12-02
You were asked for a user and a password during the install. That is the super-user. To run things with root privileges, use that user account and type "sudo" or "gksudo" for gnome applications. You can also type "sudo -i" for a root prompt.

More about this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Lvcoyote on 2007-12-02
Ok, thanks for the quick responses, appreciate it.  So if I want to browse the file system and make a change to something, whats the best way to start the process so I can edit things???

---

### Post by Lvcoyote on 2007-12-02
Nevermind - sudo nautilus works a champ!!

---

### Post by aysiu on 2007-12-02
> **Lvcoyote said:**
> Nevermind - sudo nautilus works a champ!!
Please use ```
gksudo nautilus
``` instead

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Lvcoyote on 2007-12-02
> **aysiu said:**
> Please use ```
gksudo nautilus
``` instead

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Gotcha, thanks for the quick help and information guys.  I've heard a lot of good things aboutUbuntu 7.10, thought I'd give it a try.  If these forums are any indication, it will be a great experience!!

Thanks again!

---

