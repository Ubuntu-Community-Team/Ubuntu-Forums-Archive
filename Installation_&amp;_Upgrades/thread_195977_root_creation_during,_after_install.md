---
title: "root creation during, after install"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by Donald F. Robertson on 2006-06-13
I successfully installed Ubuntu to an OQO -1 ([www.oqo.com)](www.oqo.com)).  However, during install, I was never asked for a root password.  There appears to be a root user, but it has the same password I use to log in, with no rights.  If I enter "root" as the login name, the password is ignored; appearently the only way in is with my user name and that password.  

First, is this a "feature" or a "problem"?  Is there any reason to have a separate root user in Ubuntu's flavor of linux?  Should I attempt to set one up with the Users and Groups applit?

Thanks!

-- Donald

---

### Post by johnc4510 on 2006-06-13
Ubuntu does not use root by default. If you want to gain root privledges in Ubuntu, open a terminal:Applications>Accessories>Terminal , and type sudo before your command. Then enter your regular user password at the prompt. This will give short term root access.

---

### Post by Donald F. Robertson on 2006-06-13
Unfortunately, that doesn't help.  I'm trying to install a third-party application (Moneydance), and since I don't have root privileges to all the directories it needs to use, I can't install it.  How do I give myself global root privileges?

Thanks!

-- Donald

---

### Post by johnc4510 on 2006-06-13
Okay, here is a wiki on it:
[https://wiki.ubuntu.com/RootSudo?highlight=%28root%29](https://wiki.ubuntu.com/RootSudo?highlight=%28root%29)

---

### Post by Donald F. Robertson on 2006-06-13
Thank you very much, John,

The Run as different user command worked.

-- Donald

---

