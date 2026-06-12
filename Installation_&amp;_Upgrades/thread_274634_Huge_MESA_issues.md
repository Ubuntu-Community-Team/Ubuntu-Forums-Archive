---
title: "Huge MESA issues"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-10-10
First a little history:
About 3months ago when I still didn't have a clue about all those dependencies warnings I was hapilly adding new repos and installing packages which also updated dependencies. Such packages include: XGL from QUINNs repo, BMPx, ...
So it was not long after some odd problems started to appear. Like "gnome-core-devel" wouldnt install because the dependecies were newer than GNOME-CORE-dEVEL would work with and so on.
And so a month ago I decided to get rid of XGL,BMPx with the help of "debfoster" so that also the unneded packages were removed. 
Everything went fine. So then I also uninstalled FGLRX driver which wasn't needed anymore. So I uninstalled it and did which was suppose to revert back to the mesa driver:
**sudo apt-get install --reinstall libgl1-mesa**
but here is the error I get now:
```
root@tomi:/usr/lib# sudo apt-get install --reinstall libgl1-mesa
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  libgl1-mesa
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/162kB of archives.
After unpacking 500kB of additional disk space will be used.
(Reading database ... 103596 files and directories currently installed.)
Unpacking libgl1-mesa (from .../libgl1-mesa_6.4.1-0ubuntu8_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu8_i386.deb (--unpack):
 error creating symbolic link `./usr/lib/libGL.so.1': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
and I also tried:
**root@tomi:/usr/lib# sudo aptitude install -f libgl1-mesa**
```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  libglide3
The following NEW packages will be installed:
  libgl1-mesa
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/162kB of archives. After unpacking 365kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 103596 files and directories currently installed.)
Unpacking libgl1-mesa (from .../libgl1-mesa_6.4.1-0ubuntu8_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu8_i386.deb (--unpack):
 error creating symbolic link `./usr/lib/libGL.so.1': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libglu1-mesa:
 libglu1-mesa depends on libgl1-mesa | libgl1; however:
  Package libgl1-mesa is not installed.
  Package libgl1 is not installed.
  Package libgl1-mesa which provides libgl1 is not installed.
dpkg: error processing libglu1-mesa (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libglu1-mesa

```
what can I do? I have a bunch of unresolved dependencies now. And they wont get fixed because LIBGL1-MESA isn't installed but LIBGL1-MESA also refusees to install.

ps. root@tomi:/usr/lib# locate libGL.so.1
returns nothing

---

### Post by podunk on 2006-10-10
I don't really know anything about how to help with this – but it sounds like you have an older ATI card? Why would you want to reinstall the mesa driver? It doesn't really support ATI cards, my system ran much faster after I installed the fglrx driver.

I started about 3 months ago too, and I went along installing the latest and greatest also. :-D I broke stuff right and left. Several times I got things so screwed up that everything I did to fix one problem spawned 3 or 4 more.

In the end I found it was easier and faster to just pull the plug and reinstall the OS. Of course, the first thing I would do was start to reinstall the latest and greatest, so I repeated this process several times. 

I slowed down this time. I got the core up and backed this puppy up. Now I can afford to play a little bit, if I break something I can restore it easily.

---

### Post by ashrack on 2006-10-10
my GPU is not that old! I have a Radeon9800PRO and for XGL U need FGLRX drivers. 
But still my issue remains, how to fix it>

---

### Post by ashrack on 2006-10-11
anyone?
Am kinda desperate since I cant install anything now. Not even the updates.
And the updates manager tells me to do:
[B]sudo apt-get install -f
[/B]
but this is the error I get then:
```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  libgl1-mesa
The following NEW packages will be installed
  libgl1-mesa
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/162kB of archives.
After unpacking 500kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 103596 files and directories currently installed.)
Unpacking libgl1-mesa (from .../libgl1-mesa_6.4.1-0ubuntu8_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu8_i386.deb (--unpack):
 error creating symbolic link `./usr/lib/libGL.so.1': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ashrack on 2006-10-11
bump

---

### Post by ashrack on 2006-10-12
bump

---

