---
title: "Feisty Frustration"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by Paradoxed on 2007-04-02
Good day all,

Have upgraded to Fesity and system hangs on boot. However the recovery mode works perfectly. 


 The following errors

/etc/rc2.d/s10 acpid :line 54 : 4357 segementation fault

So had a look at the above

this from line 51
if [ -n "$MODULES" ]; then
log_begin_msg "Loading ACPI modules..."
STATUS=0
for mod in $MODULES; do


Another issue on bootup is modprobe acer_acpi   FATAL


Any help appreciated

---

### Post by Majorix on 2007-04-02
Hmm... A segfault...

Your comp is trying to access a module that's likely non-existant or broken. And that module is called acpi.

Since you can run the pc in recovery mode, do that, and once in there, open up a console and type in
```
sudo apt-get install acpi
```

If it installs, then fine. If not, come and post the error(s) here.

Good luck.

---

### Post by Paradoxed on 2007-04-02
deep breathe...

Alright so I downloaded acer_acpi-0.3 
I then 

So now I see 

/home/steve/download# ls -l
total 28
drwxr-xr-x 3 steve steve  4096 Sep 22  2006 acer_acpi-0.3
-rw-r--r-- 1 root  root  24091 Sep 23  2006 acer_acpi-0.3.tar.gz

Now 

/home/steve/download# tar zxvf acer_acpi-0.3.tar.gz

acer_acpi-0.3/
acer_acpi-0.3/NEWS
acer_acpi-0.3/Makefile
acer_acpi-0.3/README
acer_acpi-0.3/AUTHORS
acer_acpi-0.3/INSTALL
acer_acpi-0.3/acer_acpi.c
acer_acpi-0.3/COPYING
acer_acpi-0.3/.tmp_versions/
acer_acpi-0.3/.tmp_versions/acer_acpi.mod
acer_acpi-0.3/acer_acpi.mod.c
acer_acpi-0.3/.acer_acpi.o.cmd
acer_acpi-0.3/acer_acpi.o
acer_acpi-0.3/acer_acpi.mod.o
acer_acpi-0.3/.acer_acpi.mod.o.cmd
acer_acpi-0.3/acer_acpi.ko
acer_acpi-0.3/.acer_acpi.ko.cmd

Now when I modprobe I get

/home/steve/download# modprobe acer_acpi
FATAL: Module acer_acpi not found.

Part 2

On reboot the following error 

/etc/rc2.d/s10 acpid:line54:4357 segmentation fault   modprobe -b $mod2> /dev/null
 this is followed by
modprobe:warning: not loading blacklisted module ipv6
Please help:confused:

---

### Post by justin whitaker on 2007-04-02
The module is not loaded because it is not compiled. 

Use VI (or whatever text editor you like) and follow the directions in the readme (probably something like make, make clean, make install etc...) and run insmod to insert acpi into the kernel. You may want to consider recompiling the kernel to include the module so you do not have to do that each boot.

Oh, and apt-get install build essential if you have not already. :)

---

### Post by Pistolpete2 on 2007-04-04
I follow the README en I compile without any errors but stil it won't work. It looks like when compiling in feisty it generates less files then in dapper

---

### Post by robz0rz on 2007-04-04
I'm pretty new to the Linux scene, and I don't know whether I'm the right person to suggest help, but I've had trouble with a faulty acpi in my BIOS as well.

Try using the bootparameter *acpi=off* and see if it boots then :)

---

### Post by Pistolpete2 on 2007-04-05
I don't think I was clear enough (my fault). I don't have the booting problem but I need acer-acpi to make my wireless work. But the strange thing is I can connect to an unprotected wireless network but not to one protected with wpa!:confused: Especially strange because I'm using Network manager who can handle wpa.

So maybe its not acer-acpi that is the problem on my system so I shouldn't be posting here?

---

### Post by anubhavrocks on 2007-04-05
> **Paradoxed said:**
> deep breathe...

Alright so I downloaded acer_acpi-0.3 
I then 

So now I see 

/home/steve/download# ls -l
total 28
drwxr-xr-x 3 steve steve  4096 Sep 22  2006 acer_acpi-0.3
-rw-r--r-- 1 root  root  24091 Sep 23  2006 acer_acpi-0.3.tar.gz

Now 

/home/steve/download# tar zxvf acer_acpi-0.3.tar.gz

acer_acpi-0.3/
acer_acpi-0.3/NEWS
acer_acpi-0.3/Makefile
acer_acpi-0.3/README
acer_acpi-0.3/AUTHORS
acer_acpi-0.3/INSTALL
acer_acpi-0.3/acer_acpi.c
acer_acpi-0.3/COPYING
acer_acpi-0.3/.tmp_versions/
acer_acpi-0.3/.tmp_versions/acer_acpi.mod
acer_acpi-0.3/acer_acpi.mod.c
acer_acpi-0.3/.acer_acpi.o.cmd
acer_acpi-0.3/acer_acpi.o
acer_acpi-0.3/acer_acpi.mod.o
acer_acpi-0.3/.acer_acpi.mod.o.cmd
acer_acpi-0.3/acer_acpi.ko
acer_acpi-0.3/.acer_acpi.ko.cmd

Now when I modprobe I get

/home/steve/download# modprobe acer_acpi
FATAL: Module acer_acpi not found.

Part 2

On reboot the following error 

/etc/rc2.d/s10 acpid:line54:4357 segmentation fault   modprobe -b $mod2> /dev/null
 this is followed by
modprobe:warning: not loading blacklisted module ipv6
Please help:confused:

Instead of 
/home/steve/download# modprobe acer_acpi

try this 
/home/steve/download#sudo insmod ./acer_acpi.ko

---

### Post by anubhavrocks on 2007-04-05
her i am assuming that "acer_acpi.ko"  is in  "/home/steve/download"  directory,if it is somewhere else please use that path.

---

### Post by Pesho on 2007-04-09
See this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96480](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96480)

---

