---
title: "ubuntu software center is telling me that another software manager needs to quit"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by damiangonzales93 on 2009-11-29
ubuntu software center is telling me that another software manager needs to quit but its the only one up

---

### Post by dhavalbbhatt on 2009-11-29
Are you sure? Usually, synaptic and apt-get (command line) are also considered software managers. If you still encounter issues, you can use the following command in the terminal to see all running processes -

ps -x

---

### Post by phillw on 2009-11-29
> **dhavalbbhatt said:**
> Are you sure? Usually, synaptic and apt-get (command line) are also considered software managers. If you still encounter issues, you can use the following command in the terminal to see all running processes -

ps -x
Also Update manager will cause the lock file.

Regards,

Phill.

---

### Post by theozzlives on 2009-11-29
try
```
sudo dpkg --configure -a
```
sometimes Update Manager gets stuck.

---

### Post by issih on 2009-11-29
If you really do not have any of the things the others posted open then look at this:

[http://ubuntuforums.org/showthread.php?t=1314612](http://ubuntuforums.org/showthread.php?t=1314612)

It seems that the ubuntu software centre reports this error (wrongly!) when its repository list is in a bad state etc.

Hope that helps

---

### Post by dhavalbbhatt on 2009-11-29
> **phillw said:**
> Also Update manager will cause the lock file.

Regards,

Phill.
Yes, absolutely.

Many thanks!

DB

---

