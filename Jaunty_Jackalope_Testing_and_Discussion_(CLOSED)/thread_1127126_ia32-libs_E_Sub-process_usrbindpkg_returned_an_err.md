---
title: "ia32-libs E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2009-04-16
I just upgraded from Intrepid to Jaunty (again) and I'm ahving trouble getting ia32-libs installed.

I had everything working perfectly fine before and decided to do a clean install to free up some hard drive space. Now I'm getting an error that I can't get around while trying to get flash and the nspluginwrapper installed.

Here is what's going on. I tried installing the restricted extras and ran into this error, but now I'm just trying to install the ia32-libs alone:

```

kyleabaker@kyleabaker-desktop:~$ sudo apt-get install ia32-libs 
[sudo] password for kyleabaker: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.0MB of archives.
After this operation, 128MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com jaunty/universe ia32-libs 2.7ubuntu4 [28.0MB]
Fetched 28.0MB in 13s (2139kB/s)                                               
(Reading database ... 113706 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.7ubuntu4_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.7ubuntu4_amd64.deb (--unpack):
 unable to create `./usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.7ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
kyleabaker@kyleabaker-desktop:~$

```

If I run update after that then I keep getting this error, but it goes away when I "clean" apt. What do I need to do to get it to install smoothly?

---

### Post by kyleabaker on 2009-04-16
I'm still unable to find a solution or get this installed. Any tips?

---

### Post by kyleabaker on 2009-04-16
This error isn't making any sense. Why will v2.7 not install since it's obviously > than 2.2 and 2.4?

```
kyleabaker@kyleabaker-desktop:~$ sudo apt-get install nvidia-glx-180
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-180 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-installer: Depends: ia32-libs (>= 2.2ubuntu18) but it is not going to be installed
  nspluginwrapper: Depends: ia32-libs (>= 2.4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by crjackson on 2009-04-16
Did you try to fix the broken cache by opening a terminal and running:
```
sudo apt-get -f install
```

---

### Post by kyleabaker on 2009-04-17
> **crjackson said:**
> Did you try to fix the broken cache by opening a terminal and running:
```
sudo apt-get -f install
```

First of all, thank you for being the first Ubuntu enthusiast to attempt to help me. No one else seems to either care or they just don't want to type out how to fix this. :P

I just attempted to install it again and immediately tested your suggestion. I'm not sure if that should fix it or not, but here is the output:

```
kyleabaker@kyleabaker-desktop:~$ sudo apt-get install ia32-libs 
[sudo] password for kyleabaker: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/28.0MB of archives.
After this operation, 128MB of additional disk space will be used.
y(Reading database ... 
113710 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.7ubuntu4_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.7ubuntu4_amd64.deb (--unpack):
 unable to create `./usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.7ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
kyleabaker@kyleabaker-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by jfernyhough on 2009-04-17
It sounds like a packaging error. Have you looked on Launchpad to see if anything has been reported for this package?

--edit

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs](https://bugs.launchpad.net/ubuntu/+source/ia32-libs)

Ah ha - just looked and what do you know:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/270327](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/270327)

[quote=captive]I solved it removing nvidia-glx, installing ia32-libs and re-installing nvidia-glx[/quote][quote=Javier García Díaz]I had the same problem to install ia32-libs, but I was using nvidia-glx-177. I solved the problem using Brian's workaround:
sudo aptitude reinstall nvidia-glx-180
sudo apt-get install ia32-libs[/quote]


--pre-edit
for posterities sake:

There may be a workaround to make it install, though this will likely cause problems as we're putting a placeholder file in rather than the real thing:

$ sudo mkdir /usr/lib32/
$ sudo touch /usr/lib32/libGL.so.1.2
$ sudo aptitude install ia32-libs

This should allow dpkg to find the file it's tripping up on at the moment, but as I say it's a placeholder. I'm assuming libGL.so.1.2 has been superseded by another libGL but the installer script hasn't been updated - or the packaging is wrong.

---

### Post by kyleabaker on 2009-04-17
The method that Javier García Díaz provided worked flawlessly. Thanks for the help guys!

Here it is again if anyone else runs into this problem.
[QUOTE=Javier García Díaz]I had the same problem to install ia32-libs, but I was using nvidia-glx-177. I solved the problem using Brian's workaround:
sudo aptitude reinstall nvidia-glx-180
sudo apt-get install ia32-libs[/QUOTE]

Substitue 180 with the version you have currently installed of course. ;)

---

