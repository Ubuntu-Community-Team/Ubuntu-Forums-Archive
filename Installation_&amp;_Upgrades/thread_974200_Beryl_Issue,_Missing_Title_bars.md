---
title: "Beryl Issue, Missing Title bars"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by PjGorton on 2008-11-07
Hey guys, I'm new to these forums therefore I'm sorry if this is the wrong section for this(or if this is even allowed).

I installed ubuntu for the first time 2 days ago, primarily to experience the amazing visual effects of Beryl. But for some reason every time i make Beryl my windows manager i loose the title bars and exit/minimize/restore buttons. 

Details:
Running: Ubuntu 8.10 on Dell inspiron 530 w/ Beryl Fiesty
Graphics card: Nvidia 


Courses of action:
Made sure the "Windows Decoration" box was ticked.
Made sure i have Nvidia Drivers.
And a few other things like restarting and stuff, nothing major.

Any help greatly appreciated, Thanks in advance.


-pj

---

### Post by tuxxy on 2008-11-07
By Beryl windows manager you mean Emerald for Compizfusion? what happens if you run this command

```
emerald --replace
```

You may need to download emerald after activating effects, you can also select and edit themes too

```
sudo apt-get install emerald
```

---

### Post by PjGorton on 2008-11-07
when i type the first commands nothing happens unfortunately.

and the second one i get...

```
pj@pj:~$ sudo apt-get install emerald
[sudo] password for pj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emerald is already the newest version.
emerald set to manually installed.
The following packages were automatically installed and are no longer required:
  libopenal1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by PjGorton on 2008-11-07
Somebody suggested that i add-argb-glx-visuals so this is what i did..


```

pj@pj:~$ sudo apt-get install nvidia-glx
[sudo] password for pj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is a virtual package provided by:
  nvidia-glx-96 96.43.09-0ubuntu1
  nvidia-glx-71 71.86.04-0ubuntu10
  nvidia-glx-177 177.80-0ubuntu2
  nvidia-glx-173 173.14.12-1-0ubuntu4
You should explicitly select one to install.
E: Package nvidia-glx has no installation candidate

```

so i could not continue. This is extremely frustrating.

---

### Post by PjGorton on 2008-11-07
Bump, Still can't get it to work.

---

### Post by PjGorton on 2008-11-07
i managed to get them to show up for a while but now there gone again.

Does **anyone** have any ideas? I am almost ready to go back to vista.

---

