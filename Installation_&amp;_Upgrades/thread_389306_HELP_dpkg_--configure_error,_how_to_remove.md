---
title: "HELP: dpkg --configure error, how to remove ?"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by adieb on 2007-03-20
hello

i tried to install clvm once, but there occured an error while trying to configure it. nevermind, thats not important, but now, when i use apt, it always tries to configure it again.

even when i try to "apt-get remove" it, it doesn´t work, because of a pre-removal script, that tries to stop the init.d/clvm-deamon which doesn´t exists or is not running.

how to solve this?

or where can I find those scripts, so i could just comment out that procedure.

thanx

---

### Post by taurus on 2007-03-20
What if you run

```
sudo aptitude --purge remove **package_name**
sudo aptitude --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by adieb on 2007-03-21
well i tried those things, but the problem ist just, that --configure -a exits with an error, and every removing trial exits with an error of a pre-removal script, that tries to stop a daemon that doesn´t exist.

so i think the only way is to edit that pre-removal script manually. but i don´t know where to find it.

anybody knows?

---

### Post by adieb on 2007-03-21
SOLVED

ok i´ve found a workaround. teh pre-removal script stopped because of an error msg of the /etc/init.d/clvm stop script.

so i just commented out the line where the sript actually tries to stop that daemon, and then there was no error reported anymore and it could be removed by apt.

maybe that´s not the gentle way of solving things but it worked and the annyoing message after every installation by apt disappeared.

bye

---

