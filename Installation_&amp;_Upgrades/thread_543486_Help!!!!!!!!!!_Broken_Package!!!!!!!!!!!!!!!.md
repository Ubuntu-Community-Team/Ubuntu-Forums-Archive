---
title: "Help!!!!!!!!!! Broken Package!!!!!!!!!!!!!!!"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by Zero_Cool on 2007-09-05
HELPPPPPPPP I have a broken package that of course needs to be fixed! When i go to try and fix using sudo apt-get install -f i get:

:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

When i go to manually run 'dpkg --configure -a' i get:

:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

I'm currently trying to install Frostwire which is what got me in this mess.... I'm fairly new to Linux, but i can catch on very quickly as to what to do... 

I'm not sure how to search for the broken file in Synaptic so if that would be easier please inform me....

---

### Post by Sensenseppl on 2007-09-05
I can't specifically help you with the broken package problem, because I never had something like that, but:
```
:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
```

suggests doing:
```
:~$ **sudo **dpkg --configure -a
```

for executing the command with superuser privileges.

I hope this brings you one step further.

---

### Post by Zero_Cool on 2007-09-05
Typed it in and brought up:


sudo dpkg --configure -a
Password:
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

re-entered sudo apt-get install -f and pulled up Java configuring.... I can not get past this screen tho.

---

