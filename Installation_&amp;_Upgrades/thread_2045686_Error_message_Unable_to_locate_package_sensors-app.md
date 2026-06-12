---
title: "Error message: Unable to locate package sensors-applet"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by pierreu1 on 2012-08-21
In order to use a [fix]("http://ubuntuforums.org/showthread.php?p=9197545#post9197545") a fan issue on a Toshiba laptop that's supposed to work, I get this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'google.listgksu' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google.listgksu' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
**[B]E: Unable to locate package sensors-applet**[/B]

What should I do?

Thank you!

[http://ubuntuforums.org/showthread.php?p=9197545#post9197545](http://ubuntuforums.org/showthread.php?p=9197545#post9197545)

---

### Post by drmrgd on 2012-08-21
That thread is very old, and as such that package is no longer available.  I'm not sure the exact replacement for it, and someone with a little more knowledge may have a better suggestion on how to get the fan working well.  

As far as sensors go, and again I'm not sure this is an exact replacement, I've used the 'lm-sensors' package, which seems to do something similar.  A little more updated information about Sensor detection:

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by pierreu1 on 2012-08-21
> **drmrgd said:**
> That thread is very old, and as such that package is no longer available.  I'm not sure the exact replacement for it, and someone with a little more knowledge may have a better suggestion on how to get the fan working well.  

As far as sensors go, and again I'm not sure this is an exact replacement, I've used the 'lm-sensors' package, which seems to do something similar.  A little more updated information about Sensor detection:

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Hi There, 

Thanks for the info! You are right! BUt, my computer is very old! :)

Anyway, I did try to install lmsensors, but I get this:


E: Unable to locate package lmsensors

Maybe ubuntu software will be nicer to me!

Any ideas?

---

### Post by pierreu1 on 2012-08-21
I used flint to see what is going on with my system. I am a newbie, but do I need all those files as seen on the screenshots? This seems strange. Surely I do not want to remove the #24 of the linux image. Right? ... In system info I am told that this is the linux version I use.

Apparently I do have lmsensor installed, according to ubuntu software!

---

### Post by pierreu1 on 2012-08-21
> **drmrgd said:**
> That thread is very old, and as such that package is no longer available.  I'm not sure the exact replacement for it, and someone with a little more knowledge may have a better suggestion on how to get the fan working well.  

As far as sensors go, and again I'm not sure this is an exact replacement, I've used the 'lm-sensors' package, which seems to do something similar.  A little more updated information about Sensor detection:

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

OKay! I think ... think that I am not completely doing all that there needs to be done to make things work.


Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

Okay! WHen I ran sensor detect, 3 modules where okayed!

coretemp
smsc
edid eeprom

I check using lsmod if they were there. The first one was! So, I think I need to load the other 2. Right?

---

### Post by drmrgd on 2012-08-22
> **pierreu1 said:**
> I used flint to see what is going on with my system. I am a newbie, but do I need all those files as seen on the screenshots? This seems strange. Surely I do not want to remove the #24 of the linux image. Right? ... In system info I am told that this is the linux version I use.

Apparently I do have lmsensor installed, according to ubuntu software!


So many older versions of the Linux kernel aren't really needed.  They don't do any harm other than taking up HDD space.  In reality, you probably don't need any more than the current kernel version, and maybe the next oldest one just in case you have an issue and need to revert to it.

In regard to the sensors, I'm glad you got it working.  Unfortunately, I'm still learning how they work and what you can do with them (I just upgraded from a very old computer that didn't have very much monitoring capability at all!).  So, we'll have to let an expert comment on just what is needed next to get better fan control.

---

