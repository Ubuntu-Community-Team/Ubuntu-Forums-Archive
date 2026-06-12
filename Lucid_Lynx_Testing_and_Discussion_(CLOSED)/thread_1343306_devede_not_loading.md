---
title: "devede not loading"
date: 2009-12-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2009-12-01
i have installed devede and when i load it, it is complaining that i have to install mplayer to use it. 

i have already installed mplayer and it is still saying install it. 

i have tried reinstalling devede and mplayer. 
i have also trued completely removing mplayer and devede with all dependencies and then reinstalling them. 

any ideas 
thanks

---

### Post by SevenMachines on 2009-12-01
this is bug in openal with a broken pulse backend. devede then calls mplayer -v but gets an error so triggers the "can't find mplayer" message and fails.
if you open /etc/openal/alsoft.conf
and remove 'pulse' from the drivers= section it should work. 
is there a bug open on openal about this yet?

$mplayer -v
...

Inconsistency detected by ld.so: dl-close.c: 731: _dl_close: Assertion `map->l_init_called' failed!

---

### Post by SevenMachines on 2009-12-01
see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=551935](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=551935)

---

### Post by SevenMachines on 2009-12-01
ah, 
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/486414](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/486414)

---

### Post by terry_gardener on 2009-12-01
sadly this didnt fix it. still get the same error, needs mplayer

---

### Post by SevenMachines on 2009-12-01
if you dont have  /etc/openal/alsoft.conf or a per user conf file ~/.alsoftrc you can create it using using /usr/share/doc/libopenal1/examples/alsoftrc.sample.gz 

and then remove the pulse driver
-#drivers = alsa,oss,solaris,dsound,winmm,port,pulse,wave
+drivers = alsa,oss,solaris,dsound,winmm,port,wave

---

### Post by SevenMachines on 2009-12-01
> **terry_gardener said:**
> sadly this didnt fix it. still get the same error, needs mplayer
what do you get when you run mplayer -v?

---

### Post by SevenMachines on 2009-12-01
i've attached .alsofrc that cures the problem for me, does it work (both mplayer and devede are fixed with this one change here) if you put this in your home directory

---

### Post by cariboo on 2009-12-02
Thank you it worked for me.

---

### Post by Yes_It's_Me on 2009-12-02
Yes, thankyou. I've had the issue for weeks now and it's good to have a solution.

---

### Post by terry_gardener on 2009-12-02
> **SevenMachines said:**
> i've attached .alsofrc that cures the problem for me, does it work (both mplayer and devede are fixed with this one change here) if you put this in your home directory

thank you this worked for me.

great work

---

