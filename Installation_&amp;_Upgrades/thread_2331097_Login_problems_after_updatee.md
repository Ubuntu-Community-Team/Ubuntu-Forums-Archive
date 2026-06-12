---
title: "Login problems after updatee"
date: 2016-07-18
forum: Installation &amp; Upgrades
---

### Post by KieranFitzgerald on 2016-07-18
After recent update to 14.04 I can't log into the desktop.  The system keeps asking for my password.  All was well before the update.  Please help.

---

### Post by Bashing-om on 2016-07-18
KieranFitzgerald; Hello;

> **KieranFitzgerald said:**
> After recent update to 14.04 I can't log into the desktop.  The system keeps asking for my password.  All was well before the update.  Please help.

Many times we see this condition as a result of a broken proprietary graphic's driver. This driver is built against the old kernel. (proprietary is NON-ubuntu)

What results when you do boot from grub with an older kernel ?
If you can boot successfully with the older kernel, we see what it will take to install the graphic's driver for the latest kernel.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by bapoumba on 2016-07-18
One other possibility is you are running out of space after the upgrade. To test, hit <ctrl><alt><f1>, login then run :
```
df -h
df -i
```

---

### Post by KieranFitzgerald on 2016-07-19
Tried 3 previous kernels same behaviour.  Oldest was 3.13.0.88-generic. Can't see any problems with space.

---

### Post by KieranFitzgerald on 2016-07-19
Any help would be most appreciated. Live boot from USB works.

---

### Post by Bashing-om on 2016-07-19
KieranFitzgerald; Yuk;

Next is can you boot to a console interface . At the login screen key combo ctl+alt+F1 .
Login here to the system.

In terminal command output:
```

sudo lshw -C display

```
in the configuration line .. is a driver listed ?
as in for my system:
> 
configuration: driver=radeon latency=0
 where my driver is "radeon".

else, we look elsewhere .

[INDENT][INDENT]one poke at a time
[/INDENT][/INDENT]

---

### Post by KieranFitzgerald on 2016-07-19
No response to terminal unless I use f1 instead of t. 
 Response to lshw command starts 
display UNCLAIMED etc including 
product GK104 GeForce GTX 660 Ti. 

> configuration : latency= 0

No driver?

 Is this relevant using the terminal from f1?  Note edit to my last post.
Kieran

---

### Post by Bashing-om on 2016-07-19
KieranFitzgerald; Well ..

Yeah .. that do say there is no graphics driver loaded .
So what driver do you want to use ?
Open source or Nvidia'a ?
Be aware that nvidia recommends the 367 version driver for that card:
[http://www.nvidia.com/download/driverResults.aspx/105343/en-us](http://www.nvidia.com/download/driverResults.aspx/105343/en-us)

However, that driver version is not available in 14.04 as the X-server in 14.04 will not support it.
The best we can do is 364 from our trusted PPA.

That is not to say that a proprietary driver available in the software repository will not function to suit your needs.
wont hurt to try:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers list

```

If you find that the drivers listed are acceptable ...
Then let the system install what it thinks best:
```

sudo ubuntu-drivers autoinstall

```

reboot to see the effect.

[INDENT][INDENT]else we do something else
[/INDENT][/INDENT]

---

### Post by KieranFitzgerald on 2016-07-20
The drivers list returns the following

> nvidia-304
nvidia-340
nvidia-352
(repeated with -update)


then tried autoinstall which during installation prompts to disable UEFI secure boot.  I messed this up by pressing the wrong key when entering a password request.
I think I had the same problem when I did the original update!

Should I retry the autoinstall again with the drivers offered.

---

### Post by Bashing-om on 2016-07-20
KieranFitzgerald; Sure;

Let's try again ..
I do not know what to advise about UEFI; every manufacturer implements the firmware different.

You want to try the 352 version driver, see how it performs for you in your use case.
I do expect that the installer will choose the 352 driver.
Clean up the prior driver install attempts first.
```

sudo apt purge nvidia*
sudo ubuntu-drivers autoinstall

```

Reboot and let's see the effect .

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by KieranFitzgerald on 2016-07-20
Up and running.  The drivers were installed but not loaded (I think).   The update requires that UEFI secure boot be disabled to use third party drivers.  The driver installation tries to take care of this but it is very easy to mess-up.  Once you reboot without disabling the secure boot you are locked out with no idea as to why.   So easy to break and hard to recover.  Fixed by reinstalling the drivers from a terminal and following the UEFI instructions VERY CAREFULLY make a mistake and you have to start again.  Thanks [COLOR=#000000]Bashing-om your help led me to the fix.[/COLOR]

---

### Post by Bashing-om on 2016-07-20
KieranFitzgerald; Great !

You do good work ..
Pleased that you gave the explicit procedure in this case.

As you have resolution:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

