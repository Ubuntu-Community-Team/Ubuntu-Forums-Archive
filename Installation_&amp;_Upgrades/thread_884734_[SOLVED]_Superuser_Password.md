---
title: "[SOLVED] Superuser Password"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by vrk1219 on 2008-08-09
Hi All,
I'm looking for a password for the super user while I'm using the 'su' command at the Konsole.

Please let me know the default su password, or let me know how I can reset it.

Regards
RK Veluvali

---

### Post by SkonesMickLoud on 2008-08-09
You'll have to hit up these guys:

[www.google.com](www.google.com)

for that one.  Breach of forum rules and all.

What do you need root for anyway?  Just use "sudo".  Which is your normal user password.

---

### Post by vrk1219 on 2008-08-09
hi SkonesMickLoud,
I'm actually issuing the password of mine, even I'm able to change the password using passwd command. (screenshot attached) But I don't know why this is not working with su/ sudo :(

---

### Post by dje on 2008-08-09
su requires the root account to be enabled which is not recommended and is against forum policy to provide instructions on how to do so (read more [here]("http://ubuntuforums.org/showthread.php?t=765414")). to get a root shell use the following:
```
sudo -i
```
or just use:
```
sudo *command*
```
when using sudo the password it requests is your users password (ie. login password)

dje

---

### Post by sisco311 on 2008-08-09
you can use *sudo -s* or *sudo -i* to start a root shell.
the root account is disabled by default.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by vrk1219 on 2008-08-09
Thanks to you all...
I apologize for the violation, which was not intentional.

Regards
RK Veluvali

---

### Post by sisco311 on 2008-08-09
If your thread is solved, please mark it solved by selecting
**Mark this thread as solved** from the **Thead Tools**.

---

### Post by intro56 on 2008-08-09
earning is easy here you should come here below
[http://managementart.blogspot.com](http://managementart.blogspot.com)

---

### Post by dje on 2008-08-09
> **vrk1219 said:**
> Thanks to you all...
I apologize for the violation, which was not intentional.

Regards
RK Veluvali

you did nothing wrong ;) so don't worry. it is against forum policy to **give instructions** on enabling the root account. 

dje

---

