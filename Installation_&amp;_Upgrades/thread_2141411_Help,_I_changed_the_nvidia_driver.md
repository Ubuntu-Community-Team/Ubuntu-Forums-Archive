---
title: "Help, I changed the nvidia driver"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2013-05-02
I upgraded to 13.04 and noticed, that the nvidia driver was not the latest (313) selected, but 304   (I think that were the numbers).

I selected the new driver, .. it took a while and after I reboot, I have only text screen, ...

I could go into my system by selecting in Grub an older version.


How can I fix that?

---

### Post by ELMIT on 2013-05-02
I tried a few things:

reboot into the new Ubuntu (3.8.0-19-generic)   => text screen with at the end saying that it needs reboot
reboot into new Ubuntu recovery   =>  same

reboot into an older version (3.5.0-27-generic), can go in

at ALT-F2 I can see the last lines referring to nvidia:

Loading extension GLX
libkmod: ERROR ../libkmod/libkmod-module.c:791 kmod_module_insert_module: could not find module by name='nvidia_313_updates'
ERROR: could not insert 'nvidia_313_updates': Function not implemented
libkmod: ERROR ../libkmod/libkmod-module.c:791 kmod_module_insert_module: could not find module by name='nvidia_313_updates'
ERROR: could not insert 'nvidia_313_updates': Function not implemented


For what I see here is, that the module is not available for the old version.
Would it  help to make it unavailable for the new kernel? How?

or any other ideas?

bye

Ronald

---

### Post by ELMIT on 2013-05-04
anybody????

---

### Post by grahammechanical on 2013-05-04
> [COLOR=#000000]reboot into an older version (3.5.0-27-generic), can go in[/COLOR]

If that is still true and you can get to a working desktop, then why not go to Additional Drivers and experiment with another driver?

Regards.

---

### Post by ELMIT on 2013-05-05
I thought on that, but I hesitate, because I don't want to lose the second way to go in as well, ...

As I know, the nvidia module is a kernel extension and fits to the kernel you are using. So if I try to use other driver settings, then I think I would just change the driver for this kernel and not the new kernel.

I believe that the modules are at a different place for each kernel and so I think it would not change anything to the new kernel, but could kick me out of my old kernel, ....

How can I make sure ???

---

### Post by ELMIT on 2013-05-05
I did as you suggested and selected the NVIDIA 304 driver as it was before.

Rebooting started with the new kernel in a graphic mode.


HOWEVER:
unity is missing

I tried:
open a terminal and type in   unity
screen refreshes but unity did not come up

The window where I started unity shows  a lot of things, ... the lines which say NOT Info or WARN are:

...
unity-panel-service: no process found
...
compiz (core) - Error: Plugin 'opengl' not loaded
...
compiz (core) - Error: Plugin 'opengl' not loaded

(yes, the Error line appeared twice)



I am not sure if that is the problem and I have no idea how to fix it.

---

### Post by ELMIT on 2013-05-11
can anybody give me some hints???

I can hardly work with that machine, since each application I start,use up the entire screen and I cannot switch to other programms, ....

---

### Post by ELMIT on 2013-06-10
This was the most annoying error I encountered ever with Linux ;-)

In my last attempt to fix it, I burned a cd to boot from this one, and NO SCREEN, all black, ...

Hours I spent and then I replaced my 19" (square) monitor with a 22" wide monitor and all works !!!

New Nvidia does not like old monitors, ....

---

### Post by ELMIT on 2013-06-13
I give up!

None of the formum admins could give me the hint how to mark this thread as solved. A new thread, I can make solved, just not this one.


SOLVED (nvidia driver)

---

