---
title: "Super User authentication failed"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by A.R.R on 2009-09-01
I am using Karmic Koala alpha 4.
Whenever I use the 'su' command and then enter my password (correctly), I get a authentication failure.

> 
[COLOR=SeaGreen]ashutoshrishi@ashutoshrishi-desktop:~/Documents/Programming$ [/COLOR]su
Password: 
su: Authentication failure
[COLOR=SeaGreen]ashutoshrishi@ashutoshrishi-desktop:~/Documents/Programming$ [/COLOR]
Also, whenever i use 'sudo' for some operation, and enter the password, I am able to run that operation with no authentication failure. 
Need information on why this is happening.
Thanks in advance.

---

### Post by nikhilk on 2009-09-01
The root account is disabled by default on Ubuntu. The recommended way to perform administrative tasks is using sudo.

Check [this]("https://help.ubuntu.com/community/RootSudo") link for details.

---

### Post by A.R.R on 2009-09-01
Thanks nikhilk!
But when I had jaunty, I could use the su command (not that i did, just for checking bash commands ;) ) with no problem. Thanks though.

---

### Post by sisco311 on 2009-09-01
> **A.R.R said:**
> Thanks nikhilk!
But when I had jaunty, I could use the su command (not that i did, just for checking bash commands ;) ) with no problem. Thanks though.

su prompts for the target user password, while sudo prompts for your user password.

i.e.:
*su -* will prompt for the root password (which is locked by default; this is why you can not authenticate as root) and *su username -* will prompt for username's password.

by default, *sudo -i*, *sudo command*, *sudo -u username command* will prompt for your user password.

for more info please read the man pages:
```
man sudo
man su
man sudoers
```

---

### Post by A.R.R on 2009-09-01
Ya, I understood where I went wrong.
When I installed 9.04 I had enabled the root account with the same password.
After that I did not do a fresh install with Karmic and therefore my root settings were reset.

---

