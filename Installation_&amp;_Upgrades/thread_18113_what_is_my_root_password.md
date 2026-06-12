---
title: "what is my root password?"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by wbeck85 on 2005-03-04
I cannot get into X after installing Ubuntu 4.10 AMD64 on my Sager np4750. I could probably figure out the problem and such, -if i could login as root. However, i cannot, because i dont know my root password. I tried running the installer and noted every prompt and never found anyprompt asking for my administrator password. So, uh, im stuck. And back in Yoper (which is pretty darn good distro, but im bored, and it doesnt have a x86_64 version)

Did i miss something?

---

### Post by bored2k on 2005-03-04
[QUOTE=wbeck85]I cannot get into X after installing Ubuntu 4.10 AMD64 on my Sager np4750. I could probably figure out the problem and such, -if i could login as root. However, i cannot, because i dont know my root password. I tried running the installer and noted every prompt and never found anyprompt asking for my administrator password. So, uh, im stuck. And back in Yoper (which is pretty darn good distro, but im bored, and it doesnt have a x86_64 version)

Did i miss something?[/QUOTE]


when asked for password use ur user password

ubuntu default uses SUDO not SU

if u wanna acquire toor passwrd type
> $sudo su 
enter ur user passwd, and then as root
> #passwd 
to specify one

ther is nuffin u cant do on su that sudo cant btw

---

### Post by Hellsteeth on 2005-03-04
Not sure if this obvious point has been missed.

Did you try the sudo command? Ubuntu, unlike most other distros does not set up a root password as part of the installation. Just put sudo infront of the command you want then when prompted, your normal password. That one specific command is then granted su access.

You can also set up a root password by 

```
sudo passwd root
```

---

### Post by Hellsteeth on 2005-03-04
2 mins behind the same answer from bored2k - we must be on the right lines then.

---

### Post by bored2k on 2005-03-04
[QUOTE=Hellsteeth]2 mins behind the same answer from bored2k - we must be on the right lines then.[/QUOTE]
lol

edit: nice jar jar binks avatar

---

### Post by wbeck85 on 2005-03-05
well, thank you very much, Im gonna make another attempt at ubuntu. That sudo command is interesting. It seems that it would kinda comprimise security in a network type enviroment though. But thank you.

BACK TO UBUNTU!

---

### Post by Slalomsk8er on 2005-03-05
I had the same problem and found the solution the root passwd is ubuntu or was it my user passwd (it was late yesterday).

---

### Post by p!=f on 2005-03-05
```

sudo -s

```
and root prompt is here without setting up the password ;)

---

### Post by crane on 2005-03-05
[QUOTE=bored2k]
ther is nuffin u cant do on su that sudo cant btw[/QUOTE]

This is not true. there are a few things you cannot do with sudo that you can with root but this should not effect the install or daily operations at all.

---

