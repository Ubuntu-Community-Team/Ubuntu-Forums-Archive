---
title: "non-standard useraccount?"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by kjbak on 2010-11-22
I need to install a program that has its own useraccount, in a nonstandard home directory, and with tcsh shell. But when I add a useraccount, the system asks only for a username, then a password, and then it immediately creates the account with standard home directory (/home/<username>), and with bash shell, before I have had opportunity to specify the other things.  When I afterwards try to change the homedirectory and shell in the "advanced" window, the system pretends to accept it, but does not change the homedirectory or shell. 

I use Ubuntu 10.04, and is ofcourse a member of the administrator group.

How do I create such a useraccount? Anybody help me?

---

### Post by xeroblast on 2010-11-22
try using the command line

```

#> adduser --home <new directory for home> <username>

```

---

### Post by louieb on 2010-11-23
and to change the default shell you can use the **chsh** command. 

please read the man page for options and warnings. (its short)

```
man chsh
```

BTW: there is an option to chance the shell through Users and Groups - I've have not used it - I use the** chsh** command.

---

