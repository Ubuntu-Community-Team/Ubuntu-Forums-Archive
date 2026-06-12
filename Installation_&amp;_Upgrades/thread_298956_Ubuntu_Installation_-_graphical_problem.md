---
title: "Ubuntu Installation - graphical problem"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by FreeLanZer on 2006-11-13
I was about to install Ubuntu on my laptop which has these specs:
Intel 1.6GHz Dual-core
1GB RAM
GeForce Go 7600
160GB HDD
The problem is:
When I boot the Live cd of Ubuntu version 6.10
I choose "Start or install Ubuntu" and it starts to load Ubuntu,
everything looks perfect until it reaches the login/(X server) and it completely messes up the graphics, it creates vertical and horizontal lines in "Ubuntu colours" (at random places from time to time), the Ubuntu boot logo remains on the screen and sometimes I even hear the startup sound. After a while it jumps out to command line only e.g. closes X.
If only I could install it somehow I could run this script:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Since I think it sounds like that will sort it out somehow, but I'm not sure what to do anyway.
Then again I would be very pleased if some of you guys could help me with this problem, any idea what to do?

---

### Post by janesfamily on 2006-11-13
Did you try booting into safe graphics mode?

---

### Post by FreeLanZer on 2006-11-13
Yeah but then I end up in the "command line" mode, I mean Ubuntu just without any GUI at all. And I don't know what to press there.

---

### Post by lazyart on 2006-11-13
from the commandline, type

sudo dpkg-reconfigure xserver-xorg

When asked for a driver, select nv, then blast thru everything else.  Once done, type

startx

and that should get you to the desktop.  If you're still having problems you can try the vesa driver... it's like a lowest common demoninator thing.  It'll work but won't do anything real fancy.  Should be be enough to run your script.

---

### Post by lazyart on 2006-11-13
Or, option two:

at the command line, type

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.1-0ubuntu1_all.deb
```

(that will download the package) then

```
sudo dpkg -i envy_0.7.1-0ubuntu1_all.deb
```

(that will install the package) and finally

```
envy
```

---

### Post by FreeLanZer on 2006-11-13
Hmmm should the command line screen look like this? :
```

 * Activating swap...                                [ ok ]
mount: Function not implemented
 * Checking file systems...
fsck 1.39 (29-may-2006)                         [ ok ]

_

```
Because when I write any of those things and hits enter nothing happens.. :-k

---

### Post by FreeLanZer on 2006-11-13
up

---

### Post by lazyart on 2006-11-13
So you've never actually logged in to the installation?

This might be a job for the Alternate CD.  Use it to do a text mode install and choose vesa as your video driver.  Then do what I mentioned above.

---

### Post by FreeLanZer on 2006-11-14
Great it worked! Now I'm in but it can't detect my network device..  dang. :neutral: 
As far as I know it's a nVidia nForce Network device of some sort, could anyone explain what I should do?

---

