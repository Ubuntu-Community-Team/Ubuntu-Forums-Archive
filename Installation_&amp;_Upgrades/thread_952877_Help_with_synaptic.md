---
title: "Help with synaptic"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by jagc on 2008-10-19
I was trying to install gtktools but the program froze and I turned off and on the computer and now everytime I try to open synaptic it says this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried writing "dpkg --configure -a" on the terminal but it says that I need superuser privileges.

What can I do?

---

### Post by gila_monster on 2008-10-19
> **jagc said:**
> I was trying to install gtktools but the program froze and I turned off and on the computer and now everytime I try to open synaptic it says this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried writing "dpkg --configure -a" on the terminal but it says that I need superuser privileges.

What can I do?

You need to run that command as root, so you need to type:

  sudo dpkg --configure -a

You will be prompted for your password. sudo is the command that you use when you need to be the superuser/root. It runs just that one command in superuser mode. Ubuntu does this as a safety feature of sorts.

---

### Post by jagc on 2008-10-19
> **gila_monster said:**
> You need to run that command as root, so you need to type:

  sudo dpkg --configure -a

You will be prompted for your password. sudo is the command that you use when you need to be the superuser/root. It runs just that one command in superuser mode. Ubuntu does this as a safety feature of sorts.


Thank you :)
It seems it works, BUT this happens:

adrian@adrian-desktop:~$ sudo dpkg --configure -a
[sudo] password for adrian: 
Configuring libmp4v2-0 (1:1.6dfsg-0.2ubuntu1) ...

Configuring gnupod-tools (0.98.3-1.1ubuntu1) ...


Nothing happens after that, is there any way I can cancel the installation of that program?

---

### Post by zvacet on 2008-10-19
It looks like configuring is done.Did you tried to run that program and see if it works?Do you have any kind of problem installing other packages?

---

### Post by jagc on 2008-10-19
> **zvacet said:**
> It looks like configuring is done.Did you tried to run that program and see if it works?Do you have any kind of problem installing other packages?

I tried to run it, but it kept saying the same, but I already fixed it.
I wrote on the terminal:

sudo dpkg --configure -a && sudo apt-get -f install

And problem solved :)

Thanks again

---

