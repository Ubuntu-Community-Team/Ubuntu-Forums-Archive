---
title: "Starting Xwindo !"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by krsnavan on 2008-06-28
Hi !

When i try to start xwindow, it says

sudo apt-get install xinit

wht package do i need to install, plz explian the procedures
and where ican get the installations

tanx

---

### Post by ibutho on 2008-06-28
Hi. To install X windows, you need to do
```
sudo aptitude update
sudo aptitude install xserver-xorg
```
You may also need to install a DE like kde, gnome or xfce.

---

### Post by krsnavan on 2008-06-28
Where can idownload the installation files

---

### Post by ibutho on 2008-06-28
You don't have to download them manually, its automatically done for you when you run apt-get or aptitude.

---

### Post by prshah on 2008-06-28
> **krsnavan said:**
> 
When i try to start xwindow, it says
sudo apt-get install xinit



From your earlier posts, it looks as though you're using ubuntu server. To add GUI functionality to this, in the terminal, give the command```
sudo apt-get install ubuntu-desktop
```

This will install and activate desktop related services as well as continue to keep your server related services active.

Post back if you need more help.

---

### Post by krsnavan on 2008-06-28
Now getting error message as

Sudo:timestamp too far in the future :jun 28 11:16:45 2008

I able to resolve dns of internet sites.

vanna

---

### Post by krsnavan on 2008-06-28
Thanx ! 
for all the help offered !

But it took long time to download xwindows from Ububtu sites, but halted at the end syaing sume file not avialable.

Whether i can get installed only the Xwindow for ubuntu from an Tar file.

Vanna

---

### Post by prshah on 2008-06-28
> **krsnavan said:**
> 
Sudo:timestamp too far in the future :jun 28 11:16:45 2008


Give the command ```
sudo -k
``` or ```
sudo -K
``` to resolve this problem.

> **krsnavan said:**
> 
Whether i can get installed only the Xwindow for ubuntu from an Tar file.


You could possibly get it from a tar file somewhere (i dont know where) but by the time you resolve dependencies and compile, you will realize that it's far better to apt-get the binaries.

If you can get hold of the live or alternate CDs of ubuntu **desktop** then post back for instructions on how you can use those to add the GUI on your installation.

---

### Post by oldos2er on 2008-06-28
What version of Ubuntu are you running?

---

