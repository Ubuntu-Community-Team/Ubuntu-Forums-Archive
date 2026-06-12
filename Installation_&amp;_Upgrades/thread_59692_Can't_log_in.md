---
title: "Can't log in"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by steven22 on 2005-08-25
Hi, Just installed ubuntu 5.04 and can not seem to go any further once i have loged in. At the end of installing the system it asks you to login and password ok. I go ahead and do that and then the following will come up [steven@budgie22:~$] and back then that was my username and password but can not go any further?. Do i need to type in something after that to activate the system or not. I can install my windows xp fine but not this ubuntu 5.04 system.Can anyone please help.

---

### Post by Daniel Rehm on 2005-08-25
It looks like you've named your workstation steven and your user account budgie22.

I'm not sure, but I think you can go "sudo passwd", which will allow you to set the root password, then "exit", and login as root with the password you just gave it, and finally "passwd budgie22" should allow you to set the password for the user account.

---

### Post by Daniel Rehm on 2005-08-25
I just tried it on my system, and I goofed. You'll still need the password after you issue the "sudo" command =-/

---

### Post by steven22 on 2005-08-25
[QUOTE=Daniel Rehm]I just tried it on my system, and I goofed. You'll still need the password after you issue the "sudo" command =-/[/QUOTE]


Thanks Daniel yeh not sure were i went wrong but has been giving me some trouble trying to install the bloody thing. Have no trouble installing windows xp. Also can u run this ubuntu system ontop of your windows xp or not?.

---

