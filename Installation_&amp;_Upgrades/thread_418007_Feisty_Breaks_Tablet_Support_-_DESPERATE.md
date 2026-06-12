---
title: "Feisty Breaks Tablet Support - DESPERATE"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by jgordon510 on 2007-04-22
I've got a Compaq TC1000 tablet pc that ran Edgy Xubuntu successfully for a while.  I upgraded to feisty and the pen is no longer working.

I have narrowed it down to a problem with the tc1k driver.  My xorg logs report:

```
(II) LoadModule: "tc1k"
(WW) Warning, couldn't open module tc1k
(II) UnloadModule: "tc1k"
(EE) Failed to load module "tc1k" (module does not exist, 0)

```

I'm getting the driver from [here.]("http://groundstate.ca/files/tc1k-1.1.tar.gz")

The file is a .o file, and I've copied it to my /usr/lib/xorg/modules/input/ directory.

What I suspect is that it needs to be a .so file to work with feisty.  I notice that all of the other input drivers are of that type and not .o files. Has something changed that would not allow a .o file to work?  Is there a way to compile the source code to make a .so file?  If there is, could someone do it for me?

---

### Post by jgordon510 on 2007-04-22
Figured it out:

From the directory with the tc1k_drv.o file:

```
gcc -shared -Wl,-soname,tc1k_drv.so -o tc1k_drv.so tc1k_drv.o -lc
```

Then copy the newly created .so file to  /usr/lib/xorg/modules/input/ 

Everything works.

I don't know how long attachments stick around, but a .tar file with the .so file in it is attached if anyone else stumbles on this problem.

---

### Post by Mickeysofine1972 on 2007-04-23
Hey

I'm new to the tc1k and i just wondered, is there antthing I need to add to the xorg.conf to get this pen to work or do i just put the .so file in the path specified?

Kind Regards

Mike

---

### Post by jgordon510 on 2007-04-26
the best guide is [this one]("http://www.rainbowbreeze.it/images/rainbow_sync/works/installations/tc1000_linux/tc1000_install.txt").

In short, you need to add a new device with a driver "tc1k".  I'll send you my xorg.conf file if you pm me.

---

### Post by Mickeysofine1972 on 2007-04-29
ok i have pm'ed you but nor reply

can you post it here?

Mike

---

