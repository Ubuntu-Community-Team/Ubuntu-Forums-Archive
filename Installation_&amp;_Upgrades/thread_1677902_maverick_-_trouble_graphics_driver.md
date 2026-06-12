---
title: "maverick - trouble graphics driver"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by nogoodnamesleft on 2011-01-29
supplied driver has poor performance on newer card

i have downloaded the latest current graphics driver from nvidia

i get a script

OK, i chmod it to executable

I sudo and run it

It says i need to stop X

Not a problem, 

sudo stop gdm

Oh dear, it doesn't stop it - the desktop shuts down to a console window, which then hangs. I think there is something else still running ...

Stopping x doesn't seem to work either

I thought you could press alt and f-keys to boot a 2nd user console?

That doesn't work either

So having trouble stopping gdm and/or with the driver

Any pointers would be greatly appreciated

Thanks !

---

### Post by realzippy on 2011-01-29
Why do you install the driver manually?
Every kernel update you had to repeat this.
Install the nvidia driver via System/Administration/HardwareDrivers..

---

### Post by nogoodnamesleft on 2011-01-29
that is an older driver with lower performance and less compatibilty with modern games

---

### Post by realzippy on 2011-01-29
Not so old,but anyway:
If you want to have the newest nvidia driver,add the xswat ppa to your software sources.
Open terminal,run (line by line):
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
After you have done this,the offered current driver available in
System/Administration/HWdrivers
will be the newest (same as from nvidia directly,270.18 ) 8)

---

### Post by nogoodnamesleft on 2011-02-01
Thanks

I've also worked out how to stop gdm on ubuntu. I was looking at docs for the old runlevel system and ubuntu uses upstart.

---

