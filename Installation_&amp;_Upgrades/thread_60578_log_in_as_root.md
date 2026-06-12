---
title: "log in as root"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by rcschmie on 2005-08-28
I was never asked at installation for a root or admin password, only for a user account which works fine.  How do I log in as root to make administrative changes??  Sorry if this is a newbie question, first time Linux user.

---

### Post by jasmuz on 2005-08-28
Most system modifications, not to say all of them, can be ajusted using sudo (wich gives you limited root powers).

---

### Post by macgyver2 on 2005-08-28
Reading this will probably help you:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Buffalo Soldier on 2005-08-28
Ubuntu uses sudo instead of enabling the root user. Hopefully these links will be helpful:[list]
[*] Ubuntu Wiki - [Sudo](https://wiki.ubuntu.com/RootSudo).
[*] [Sudo in a Nutshell](http://www.courtesan.com/sudo/intro.html)[/list]

---

### Post by izmaelis on 2005-08-28
You can't log in as root to default Ubuntu installation and if you need to do something that requires root permissions you must type
```

# sudo

```
before typing command. If you have been asked for password input password that you entered during installation of Ubuntu. It's a password of your first user.

May the force be with you!

---

### Post by votum on 2005-08-29
[QUOTE=rcschmie]I was never asked at installation for a root or admin password, only for a user account which works fine.  How do I log in as root to make administrative changes??  Sorry if this is a newbie question, first time Linux user.[/QUOTE]

Try to use ```
sudo -s
```

---

