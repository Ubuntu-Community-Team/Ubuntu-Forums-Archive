---
title: "Location of the directory of C header files that match your running Kernel ?"
date: 2013-04-10
forum: Installation &amp; Upgrades
---

### Post by qt11 on 2013-04-10
Hey guys....

I'm trying to install VM Tools into Ubuntu 12.10 however when running the /usr/bin/vmware-config-tools.pl script.

... its asking me for the "location of the directory of C header files that match your running kernel"

I've googled and found a number of solutions however none work. It looks like I need to install the headers....so

```
sudo apt-get install linux-headers-`uname -r`
```

gives :

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.5.0-17-generic
E: Couldn't find any package by regex 'linux-headers-3.5.0-17-generic'

```


and

```
apt-get install linux-headers
```

gives 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-3.5.0-17' instead of 'linux-headers'
linux-headers-3.5.0-17 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


Now, I understand my header files should be in 

```
/lib/modules/Your-Kernel/build/include
```

however 

```

root@ubuntu:/lib/modules/3.5.0-17-generic# ls
initrd               modules.ccwmap       modules.isapnpmap  modules.symbols
kernel               modules.dep          modules.ofmap      modules.symbols.bin
modules.alias        modules.dep.bin      modules.order      modules.usbmap
modules.alias.bin    modules.devname      modules.pcimap
modules.builtin      modules.ieee1394map  modules.seriomap
modules.builtin.bin  modules.inputmap     modules.softdep

```

i don't have a build dir... ?

Any ideas of where to go next.... just trying to install VM Tools.... how hard can it be ???

:(

---

### Post by Doug S on 2013-04-11
Is this what you are looking for? (done for my computer, change for yours):```
ls -l /usr/src/linux-headers-3.2.0-40-generic/include/linux
```

---

### Post by qt11 on 2013-04-11
thanks Doug, 

unfortunately not :(

```

root@ubuntu:/usr/src/linux-headers-3.5.0-17/include/linux# pwd
/usr/src/linux-headers-3.5.0-17/include/linux

```

```

Searching for a valid kernel header path...
The path "" is not valid.
Would you like to change it? [yes] 

What is the location of the directory of C header files that match your running
kernel? /usr/src/linux-headers-3.5.0-17/include/linux

The path "/usr/src/linux-headers-3.5.0-17/include/linux" is not valid.

```


I'm sure it shouldn't be this difficult to get the VM Tools installed into Ubuntu 12.10.... is it ???

Thank you :)

---

### Post by qt11 on 2013-04-11
a solution  !!!

```
[FONT=Courier New]sudo apt-get install linux-headers-$(uname -r)
```[/FONT]

:)

---

