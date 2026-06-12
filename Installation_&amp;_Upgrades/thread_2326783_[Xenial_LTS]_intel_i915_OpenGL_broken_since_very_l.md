---
title: "[Xenial LTS] intel i915: OpenGL broken since very latest libdrm/2/mesa updates ?!?!?"
date: 2016-06-04
forum: Installation &amp; Upgrades
---

### Post by GhettoGirl on 2016-06-04
[SIZE=4][COLOR=#ff0000][B]Thread is INVALID as of 5th June 2016, i uninstalled Ubuntu - switched to ArchLinux.
[/B][/COLOR][COLOR=#b22222]**[SIZE=2]Read reply to this thread for reason[/SIZE]**[/COLOR][COLOR=#ff0000][/COLOR][/SIZE]

Hi dear community.

I run into a critical problem since the last updates from _xenial-security_ repos. I had updates for **compiz**, **libdrm***, **libdrm2*** and the **mesa** libraries. After the installation I get following output from *glxinfo*:
```
Error: couldn't find RGB GLX visual or fbconfig
```
Before the upgrade everything worked. [OpenGL 3.3]

I'm no longer able run any OpenGL applications using the Intel GPU anymore. Including, but not limited to: Unity Desktop (login loop :evil: , i know it's because of broken OpenGL).
Also I'm no longer able to use Bumblebee, i guess it has something todo with the mesa updates?
```
Cannot access secondary GPU
```
PS: Also the nvidia-364 package had a update. My best guess is, to add compatibility with the libdrm updates????

Everything broke together with just a single click on the "Mark all Upgrades" button in Synaptic :evil: :-(
I've no idea what is going on.


The Xserver log isn't very co-operative aswell as the bumblebee log :(

[HR][/HR]
 I can still use the Xserver, infact I postet *this* thread using firefox on a standalone xserver. ```
xinit /usr/bin/xterm "firefox" $* -- :1 vt8
``` At least X still works^^ OpenGL doesn't!

```

Ubuntu 16.04 LTS
Kernel 4.4.10 x86_64 (i also tried 4.5.6, same results)
Intel HD Graphics iGPU
NVIDIA GTX980M dGPU

lspci output too long to paste here, i can't copy it with the current tty/x mess :(

```

I tried everything that I'm aware of, to recover from this, with no results.


[LIST]
[*]several apt (--reinstall) / dpkg-reconfigure attemps of the Xserver and the mesa and libdrm packages 
[*]trying to find solutions on the web that fit my problem 
[*]trying different kernels (PS: 4.6.1 doesn't find any HDD's or SSD's so can't boot) 
[/LIST]

What is even going on here? Does someone know? Should I do a clean reinstall and copy over the /home and /etc folder?
Any help please. I'm out of ideas...

---

### Post by GhettoGirl on 2016-06-05
After some time of thinking, I decided to leave the Ubuntu community because I don't like Ubuntu - I never liked it, I'm never going to like it. I don't know why I installed Ubuntu one year ago in the first place :/ I had openSUSE, it was my favorite distro.

Maybe one reason why I switched to Ubuntu could be that, that I wasn't able to setup Bumblebee and nVidia optimus, this times are over now - I know to much now about the Bumblebee Project and nVidia optimus - I literally could set it up from source code now :D

My new distro of choice is ArchLinux now :guitar:
I was a "funny" year :p
Goodby Ubuntu and fellow Ubuntu users.

This thread is invalid now, I don't care anymore.

---

