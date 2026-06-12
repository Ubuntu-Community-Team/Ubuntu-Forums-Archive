---
title: "Can`t log on to root!"
date: 2004-11-30
forum: Installation &amp; Upgrades
---

### Post by serviset on 2004-11-30
Can`t log on to root, because i don't know what the root-password is. Wasn`t asked for one during the installation, so, what do i do?

---

### Post by liberal_tugboat on 2004-11-30
you can't log into root because there is no root by defalt. you use the sudo command to run things you would do as root.
logging in as root is a HUGE unix/linux no no!!! 
if you really want a root account then read the how tos on ubuntulinux.com

---

### Post by jdodson on 2004-11-30
there is a root console in menu as a selection, from that console you can set the root password via 'passwd'.

you can also run:
```
sudo su
sudo passwd

``` 
to change the password.  i sometimes do rooty things using root, however i know what i am doing.  please do not do anything you do not know the full consequence of.

---

### Post by liberal_tugboat on 2004-11-30
[QUOTE=][/QUOTE]
 ever since they added the root console I have never needed to enable root. Everthing that you would need a root account for can be done with the console. Enabling the root account just opens up a can a worms that can lead to more hurt then harm, because some people new to linux/unix will just log in as root, which opens up tons of security holes (look at windows XP, where almost everyone logs on as "root" ). I say, just leave root locked and use the sudo command for common admin tasks, and the root console to ONLY if you absolutely need it!!!!! (like to install k3b)

---

