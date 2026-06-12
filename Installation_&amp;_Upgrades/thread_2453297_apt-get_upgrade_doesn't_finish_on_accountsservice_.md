---
title: "apt-get upgrade doesn't finish on accountsservice package"
date: 2020-11-06
forum: Installation &amp; Upgrades
---

### Post by sgc2c on 2020-11-06
I did a simple "apt-get update" followed by "apt-get upgrade"
which has never had any problems.
After finishing all the other updates, upgrade
just stayed there never finishing at the 
accountsservice package.  

I control-C'd out of it then followed it up with a 
"dpkg --configure -a" which also just stayed
there, apparently not doing anything of substance 
but not hung either.

_Here's some relevant information_:



root@XYZ:/home/person# dpkg --configure -a
Setting up accountsservice (0.6.40-2ubuntu11.6) ...





person@XYZ:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.7 LTS
Release:        16.04
Codename:       xenial

# uname -a
Linux XYZ 4.4.0-173-generic #203-Ubuntu SMP Wed Jan 15 02:55:01 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


What should I do?
Thanks in advance.

-sgc2c

---

### Post by TheFu on 2020-11-07
I did a **full-upgrade** this morning on about 10 different 1604 servers and didn't have any issues. The accountsservice package was part of the patching. Have you tried that or is there a reason you can  use a full-upgrade?

---

### Post by Impavidus on 2020-11-07
I don't know about your specific problem (and haven't used 16.04 in years), but I did notice that you run kernel 4.4.0-173, compiled almost 10 months ago. A fully updated 16.04 system should be on kernel 4.4.0-193 by now. It seems there's something else wrong with your package management and has been wrong for about 9 months.

Any packages that report a state other than installed, purged or remaining config? Any kernel metapackages missing?

---

### Post by deadflowr on 2020-11-07
How long did it hang?

---

### Post by TheFu on 2020-11-07
Good catches!

A properly patched 16.04 system should have either
```
$ uname -a
Linux zcs45 **4.4.0-193-generic** #224-Ubuntu SMP Tue Oct 6 17:15:28 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```
or
```
$ uname -a
Linux hadar **4.15.0-122-generic** #124~16.04.1-Ubuntu SMP Thu Oct 15 16:08:36 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```
Which depends on when the 16.04 was installed and whether HWE updates were installed or not. HWE gets the newer kernel line.

---

### Post by sgc2c on 2020-11-07
> **deadflowr said:**
> How long did it hang?


It just never finished.

---

### Post by ActionParsnip on 2020-11-08
Try:
```

sudo apt-get update 
sudo apt-get clean 
sudo apt-get upgrade 
sudo apt-get dist-upgrade

```

Please give the full output

---

### Post by TheFu on 2020-11-10
accountsservice is related to a root escalation attack, I'd bet: 
[https://arstechnica.com/information-technology/2020/11/ubuntu-fixes-bugs-that-standard-users-could-use-to-become-root/](https://arstechnica.com/information-technology/2020/11/ubuntu-fixes-bugs-that-standard-users-could-use-to-become-root/)

---

