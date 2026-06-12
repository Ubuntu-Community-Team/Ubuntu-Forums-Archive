---
title: "Update-manager wont update"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by kingof1981 on 2008-05-28
Hello Folks.

i'm sure that everybody had a such problem one time. that the update-manager wont update... In my case if i press the install button, it only read's that currently state and then happends nothing there's still the update's there. 

frix@frix-kingof1981:~$ update-manager 
current dist not found in meta-release file

My sources.list does only contain hardy sources... So what is the problem???
Thanks for helping???

---

### Post by phoenix_abhi on 2008-05-28
Why do not try it on terminal ?

---

### Post by abn91c on 2008-05-28
> **kingof1981 said:**
> Hello Folks.

i'm sure that everybody had a such problem one time. that the update-manager wont update... In my case if i press the install button, it only read's that currently state and then happends nothing there's still the update's there. 

frix@frix-kingof1981:~$ update-manager 
current dist not found in meta-release file

My sources.list does only contain hardy sources... So what is the problem???
Thanks for helping???

you actually need to do in a terminal
sudo apt-get update
sudo apt-get upgrade

if any errors appear try apt-get check , it will usually tells you what's wrong and how to fix it
also try dpkg --configure -a

---

### Post by kingof1981 on 2008-05-28
My ubuntu is conpletly updated... current status...
Ubuntu 8.04 (hardy)
Gnome 2.22.1 (Ubuntu 2008-05-07)
Kernel 2.6.24-17-generic (#1 SMP Thu May 1 14:31:33 UTC 2008)

so why this???

---

### Post by kingof1981 on 2008-05-28
frix@frix-kingof1981:~$ sudo apt-get check
[sudo] password for frix: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
frix@frix-kingof1981:~$

---

### Post by flyboy917 on 2008-05-29
> **abn91c said:**
> you actually need to do in a terminal
sudo apt-get update
sudo apt-get upgrade

if any errors appear try apt-get check , it will usually tells you what's wrong and how to fix it
also try dpkg --configure -a


K, I'm in the same boat. The above worked with the following exception:
The following packages have been kept back:
  f-spot
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Thoughts?

---

### Post by Bubba64 on 2008-05-29
You can also go into synaptic and hit reload, once in awhile my update manager doesn't work just the spinning wheel, so I use the force quit available in add ons to panels to close it and go to terminal or synaptic to check. I suspect that this update manager not working once in awhile is a bug.

---

