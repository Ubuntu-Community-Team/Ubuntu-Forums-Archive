---
title: "Nvidia 2 display resolution"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by Varlonia on 2011-05-23
Hi All,

I'm trying to get my 2 displays working in the correct resolution with a new Ubuntu 11.04 installation.

I'm able to get both displays up and running but my 22'' Display with a native resolution of 1680x1050
only runs at 1152x864 currently.
When I am starting the nvidia setup program via:
```

gksudo nvidia-settings

```I do not get a possible resolution higher then 1360x768 for this monitor.

I've also tried to change the /etc/xorg.conf file to a resolution of 1680x1050 but this results in a black screen
for my 22''.

Any help is welcome thanks,

Varlonia

---

### Post by gewin on 2011-05-24
The main issue I had with dual monitors was to make sure that "same image in all monitors" was not selected under the Monitor Preferences. If you extend the desktop over the 2 monitors you can control the resolution of each monitor separately. Unfortunately I haven't been able to make anything else work, eg shutdown the notebook monitor and use the external monitor at it's full resolution.

---

### Post by Varlonia on 2011-05-24
Hi,

Thanks for the answer but this is not my problem.
The basic setup is in place the only thing that I can not configure is the 
resolution of the 22'' display. (The default resolution for this monitor is not selectable.)

So any other Ideas?

Thanks,

Varlonia

---

