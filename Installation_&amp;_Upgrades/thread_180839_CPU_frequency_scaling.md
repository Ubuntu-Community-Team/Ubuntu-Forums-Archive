---
title: "CPU frequency scaling"
date: 2006-05-23
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-05-23
I cant get POWERNOW to work on DAPPER x32. Here are the outputs:
```
tom@lea:~$ dmesg |grep 'power'
[4294696.939000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[4294696.943000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
tom@lea:~$ sudo /etc/init.d/powernowd restart
 * Stopping powernowd:                                                   [ ok ]
 * Starting powernowd...  * CPU frequency scaling not supported
                                                                         [ ok ]
tom@lea:~$ uname -a
Linux lea 2.6.15-22-k7 #1 SMP PREEMPT Sun May 7 17:27:47 UTC 2006 i686 GNU/Linuxtom@lea:~$

``` The LAPPY is chiliGREEN D400k:
AMD Sempron 3000+, 1,8 GHz, 512 MB RAM, 60 GB disk, DVD-RW.

Ive also opened a bug report:
[https://launchpad.net/distros/ubuntu/+source/powernowd/+bug/44699]("https://launchpad.net/distros/ubuntu/+source/powernowd/+bug/44699")

---

### Post by ashrack on 2006-05-24
anyone?? Its really annoying having to work on these lappy and the fan constantly running

---

### Post by macgabhs on 2006-05-29
I was having the same issue after upgrading to Dapper from Breezy. I'm running a sony vaio with an intel pentium M 1.76GHz chip. I found the solution to be removing powernowd via synaptic then reinstalling it and rebooting. Not sure if this will work with POWERNOW-k8 too but its probable worth a try

---

### Post by panurge77 on 2006-05-29
I'm running an Athlon 64. Do I need both powernod and powernowd.early loading at boot?? What's the difference between them?

---

### Post by ashrack on 2006-05-29
[QUOTE=macgabhs]I was having the same issue after upgrading to Dapper from Breezy. I'm running a sony vaio with an intel pentium M 1.76GHz chip. I found the solution to be removing powernowd via synaptic then reinstalling it and rebooting. Not sure if this will work with POWERNOW-k8 too but its probable worth a try[/QUOTE]
it didnt help :(

---

### Post by macgabhs on 2006-05-30
I've noticed today that even though I had fixed this problem yesterday when I rebooted this morning the cpu would not scale!! Very fructrating but once again a reinstall of powernowd fixed the problem??? Weird

---

### Post by aurelieng on 2006-05-31
I'm using powersaved/kpowersaved on my Pentium-M laptop, and dynamic frequency adjustement is working perfectly :)

---

### Post by harshy on 2006-06-03
Try enabling the powernow fuction within your bios. It might be names K8 'Cool n Quiet' or somthing along those lines. On Nvidia based systems at least, if you disable the powernow in the bios, the linux kernel will not see that it has scaling capabilities.

I will warn you however, enableing this feature has the potential to hard lock the box almost right away. It will lock up at GDM once the user name is entered. If you do get into a session and go to run an application, it will lock up. This is on amd64 flavor installs and I have not tested it on 32bit installs.

---

### Post by Johnsie on 2006-06-04
**aurelieng** thanks for that little tip....

I typed:
**sudo apt-get install powersaved**

It unloaded the powernow thing and installed powersaved

**Now my laptop is working amazingly fast and not crashing :-)**

I have no idea how but I don't care :-D

---

