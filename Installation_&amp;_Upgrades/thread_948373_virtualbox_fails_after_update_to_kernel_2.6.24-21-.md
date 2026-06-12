---
title: "virtualbox fails after update to kernel 2.6.24-21-generic"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by funky_D on 2008-10-15
Hello all,
i just updated my kernel to 2.6.24-21-generic.
My virtualbox was working fine, but now this error appears.
I tried to do *sudo /etc/init.d/vboxdrv setup* but the output was [I]sudo: etc/init.d/vboxdrv: command not found
[/I]i even tried *sudo "etc/init.d/vboxdrv setup"*, and the error was *sudo: etc/init.d/vboxdrv setup: command not found*.


[HTML]VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}
[/HTML]


I'm a linux starter, does someone have any idea?
Thanks all.

---

### Post by rpw on 2008-10-15
Maybe you missed the first /, because ther error message shows no / at the start. The correct command is indeed:

sudo /etc/init.d/vboxdrv setup

Regards,

rpw

---

### Post by howefield on 2008-10-15
Is it the OSE version of virtualbox that you are using, ie, the one in the Ubuntu repository ?

Try installing the virtualbox modules for your kernel, in terminal type

```
sudo apt-get install virtualbox-ose-modules-2.6.24-21-generic
```

or search for it via Synaptic Package Manager.

Then run the command you tried earlier.

---

### Post by funky_D on 2008-10-15
hello all!
great stuff guys!


howefield: i downloaded the new modules, like you said and i ran *sudo /etc/init.d/vboxdrv setup*

all works fine!

thank you guys!

---

### Post by howefield on 2008-10-15
great, glad to hear your sorted.

:popcorn:

---

### Post by Springs on 2008-10-15
I am having a similar problem...

I am using the xVM Edition.

After the update this morning, when I try to launch VirtualBox, I get spawning session when I try to start a machine. It doesn't time out and I have to Kill the Process. 

Any help would be great.

****EDIT****
I typed this into a terminal:
sudo /etc/init.d/vboxdrv setup

Output was
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.

Now it works!

---

### Post by in_rainbow on 2008-10-16
thanks,

*sudo /etc/init.d/vboxdrv setup*

this worked for me.

---

### Post by manlypain on 2008-10-16
This also worked for me.  Thanks for the posts.  


ubuntu update spawning session virtual box

---

### Post by Arabiest on 2008-10-16
Thanks gents,

This works for me tooooo.

I am thankful to all of you out there.

---

### Post by jyanek on 2008-10-16
Excellent!  This saved my day.  Worked well.

---

### Post by oofnik on 2008-10-17
I love quick, easy fixes. Thanks :)

---

### Post by thijsemans on 2008-10-17
Thanks!!!!

---

### Post by rhenium3 on 2008-10-18
> **howefield said:**
> Is it the OSE version of virtualbox that you are using, ie, the one in the Ubuntu repository ?

Try installing the virtualbox modules for your kernel, in terminal type

```
sudo apt-get install virtualbox-ose-modules-2.6.24-21-generic
```



Just put that in, solved the problem, thanks! :)

---

### Post by loser28 on 2008-10-18
[http://www.free-prepaid.com/?id=75351748](http://www.free-prepaid.com/?id=75351748)    :lolflag:

---

### Post by booyabazooka on 2008-10-20
The latest kernel update broke virtualbox for me as well.

I'm not sure why everyone else seems to have success with vboxdrv setup, I don't...

```
sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
```

Anyway, check your kernel version.  I couldn't figure out why virtualbox-ose-modules-2.6.24-21-generic wasn't helping me, until I looked at this:

```
$uname -r
2.6.24-21-rt
```

So this is what worked for me:

```
$sudo apt-get install virtualbox-ose-modules-2.6.24-21-rt
```

---

### Post by vijaym on 2008-10-21
thanks this fix - 

sudo /etc/init.d/vboxdrv setup

worked for me.

---

### Post by mikropolip on 2010-09-06
I've got 2.6.32-24-generic and my virtualbox-ose has seaced to work after recent kernel update. 

```
$ sudo apt-get install virtualbox-ose-modules-2.6.32-24-generic
``` doesn't help since there is no such package. Any ideas?

```
$ /etc/init.d/virtualbox-ose setup
Usage: /etc/init.d/virtualbox-ose {start|stop|stop_vms|restart|force-reload|status}
``` doesn't work either since there is no "setup" command.

```
$ sudo /etc/init.d/vboxdrv setup
``` 
gives
```
sudo: /etc/init.d/vboxdrv: command not found
```

---

