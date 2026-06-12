---
title: "Help me please. I cant install anything !"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by Lisaac10 on 2010-08-01
I get this error every time i try to install something. 

guest24@isaac-desktop:~$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-22 linux-headers-2.6.32-22-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra
The following NEW packages will be installed
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 38 not upgraded.
Need to get 0B/285kB of archives.
After this operation, 778kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 85%dpkg: unrecoverable fatal error, aborting:
 files list file for package `apparmor-utils' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
guest24@isaac-desktop:~$ 



I always get that apparmor error every time i try to install something. I cant even update my pc ! Please help me ! :(

---

### Post by kerry_s on 2010-08-01
run-> sudo apt-get -f install

use synaptic gui to install things.

---

### Post by conradin on 2010-08-01
I would reboot into recovery mode and try using dpkg to repair broken packages.

---

### Post by Lisaac10 on 2010-08-01
> **kerry_s said:**
> run-> sudo apt-get -f install

use synaptic gui to install things.
I still get the same error :(

---

### Post by Lisaac10 on 2010-08-01
> **conradin said:**
> I would reboot into recovery mode and try using dpkg to repair broken packages.

Am going to give it a try

---

### Post by Lisaac10 on 2010-08-01
> **conradin said:**
> I would reboot into recovery mode and try using dpkg to repair broken packages.

How can i do that ?

---

### Post by conradin on 2010-08-01
When you reboot, you get a list of kernels, some of which say (recovery mode). Select one of those. Then a small list of options will appear, of which, one says something like repair broken packages. select that. Then boot into the shell. Then type:
```
startx
``` and hit enter. Let us know how that goes.

---

### Post by Lisaac10 on 2010-08-01
> **conradin said:**
> When you reboot, you get a list of kernels, some of which say (recovery mode). Select one of those. Then a small list of options will appear, of which, one says something like repair broken packages. select that. Then boot into the shell. Then type:
```
startx
``` and hit enter. Let us know how that goes.

While the packages were downloading the same error came out. I then started it again and when it asked me if I wanted to save it I typed startx and the root user came out. I tried updating it while on root and the same error came out.

---

### Post by conradin on 2010-08-01
Apparmor-utils may be corrupt. I would try uninstalling apparmor-utils /apparmor (completely) and then re-installing.  Ofcourse, that might not work. I'm curious if you're able to uninstall anything. 

you might find this thread helpfull:
[http://ubuntuforums.org/showthread.php?t=352049](http://ubuntuforums.org/showthread.php?t=352049)

its not exactly the same, but the advice is good.

---

