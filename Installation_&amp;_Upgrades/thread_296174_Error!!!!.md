---
title: "Error!!!!"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by momotaro on 2006-11-09
while using senaptic to add or to remove a prog at the end i have this!!!
```
E: emifreq-applet: subprocess post-installation script returned error exit status 2
```
plz help!!

---

### Post by taurus on 2006-11-09
Open a terminal, Applications -> Accessories -> Terminal, and type these two commands.  If there is an error message, paste it here...

```
sudo aptitude update
sudo patitude upgrade
```

---

### Post by momotaro on 2006-11-09
still giving me the same error:
```
E: emifreq-applet: subprocess post-installation script returned error exit status 2]
```

---

### Post by momotaro on 2006-11-09
this is what exactly i have:
```
momotaro@momotaro:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up emifreq-applet (0.18-1ubuntu3) ...
Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or built in the kernel.
invoke-rc.d: initscript emifreq-applet, action "start" failed.
dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 emifreq-applet
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up emifreq-applet (0.18-1ubuntu3) ...
Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or built in the kernel.
invoke-rc.d: initscript emifreq-applet, action "start" failed.
dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 emifreq-applet

```

---

### Post by Kateikyoushi on 2006-11-09
Which kernel and cpu do you use ?

```
uname -a
```

---

### Post by momotaro on 2006-11-09
after entering the command this is what i got:
```
Linux momotaro 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux
```

---

### Post by Kateikyoushi on 2006-11-09
With that kernel you should be able to use scaling.
Do you have powernowd installed ?

```
sudo aptitude search powernowd
```

---

### Post by momotaro on 2006-11-09
this what i got:
i   powernowd                     - control cpu speed and voltage using 2.6ke

---

### Post by cxviera on 2006-12-05
hello, im form chile and i have the exact same problem, im kind of new on this and i worried about this problem when i have to work with webs that works only with IExplorer and i can't see them without wine, so i can't install wine beacuase of this, can anyone help us please, it's really important to me at least.....
by the way great forum, i use edgy and i love it every minute of it...
Cx

---

### Post by amk221 on 2006-12-11
I also have the exact same problem, any tips or alternatives for cpu scaling appreciated

---

### Post by cxviera on 2006-12-24
i locate the emifreq applet file and erase it....that worked with no problems....at least for now...
maybe is not the best way to solve the problem but it gives me not one problem with anything in my system......great!

---

### Post by Draconous on 2007-02-24
I have a solution with this problem. I was having this for three weeks and now I just figured it out. This error message:
E: emifreq-applet: subprocess post-installation script returned error exit status 2
is the file: emifreq-applet is just a CPU monitor that just monitors the CPU temperature and contains CPU information. It's just a program, so if you uninstall it everything should update... I did that and it works for me. So, I would recommend if you have the program called Synaptic package manager, and you do a search with this file and it's there, than I would uninstall it. Once you do that you can do "sudo apt-get update" to get the updates and go from there.

---

