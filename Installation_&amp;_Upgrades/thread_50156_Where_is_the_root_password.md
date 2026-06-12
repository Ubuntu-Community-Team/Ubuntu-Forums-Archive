---
title: "Where is the root password?"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by scorpio2002 on 2005-07-19
I've just installed Ubuntu. During the installation I was asked to create a user and to set a password for him, and so I did. But I was not asked to give a password for the root user.
So basically now i can't gain root priviledges because I don't know the root password. is it normal? O_o why didn't the installer ask me for a password and set one of its own without letting me know about this?

---

### Post by codejunkie on 2005-07-19
ubuntu uses sudo insted of root so to gain root access to something for example synaptic you would open a terminal and type ```
sudo synaptic
``` and give your password instead of typing ```
su
``` then giving the root password to login as root an then running synaptic.

---

### Post by Lord Illidan on 2005-07-19
Type sudo passwd in a terminal, and set your own root password. However, root functionality in Ubuntu is limited, as it is preferred that you use sudo.
Actually, sudo uses your own password...

---

### Post by frodon on 2005-07-19
To become root in a terminal type : ```
sudo su
```a simple "su" will not work (after a fresh install your root password is your user password).

---

### Post by codejunkie on 2005-07-19
[QUOTE=Lord Illidan]Type [COLOR=Blue]sudo passwd[/COLOR] in a terminal, and set your own root password. However, root functionality in Ubuntu is limited, as it is preferred that you use sudo.
Actually, sudo uses your own password...[/QUOTE]
to enable the root user it has to be ```
sudo passwd root
```

---

### Post by WildTangent on 2005-07-19
as mentioned, Ubuntu doesnt use root by default, because its insecure. instead, whenever youre asked for a password to do something, put in YOUR password. when using the terminal, put sudo in front of any command you are required to be root for, and then put in YOUR password when it asks you. Ubuntu will remember your password for a while, so you dont need to put a pass in every time you use sudo

-Wild

---

