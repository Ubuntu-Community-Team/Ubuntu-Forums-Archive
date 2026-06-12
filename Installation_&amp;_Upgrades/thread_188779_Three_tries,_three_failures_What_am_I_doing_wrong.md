---
title: "Three tries, three failures: What am I doing wrong?"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by lakelovers on 2006-06-04
I have copied the recommended source list, did an update, then an dist-upgrade. Everything goes fine until I reach the ubuntu desktop install, and I get these errors. I commented out the unsupported universe sources on the source list, and I did not continue with the unpacking, as you can see. However, I did unpack in my attempt yesterday, and it took all day and half the night. In the end, I still not have Dapper upgraded. Hate to say it but I guess I need handholding because I can't figure it out.
```

1199 upgraded, 234 newly installed, 65 to remove and 10 not upgraded.
Need to get 29.3kB/757MB of archives.
After unpacking 350MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
jerry@Desktop:~$ sudo apt-get install ubuntu-base
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  ubuntu-base
0 upgraded, 1 newly installed, 0 to remove and 1225 not upgraded.
Need to get 12.3kB of archives.
After unpacking 41.0kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/main ubuntu-base 0.119 [12.3kB]
Fetched 12.3kB in 1s (11.0kB/s)

Preconfiguring packages ...
Selecting previously deselected package ubuntu-base.
(Reading database ... 112346 files and directories currently installed.)
Unpacking ubuntu-base (from .../ubuntu-base_0.119_all.deb) ...
Setting up ubuntu-base (0.119) ...
jerry@Desktop:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: alacarte but it is not going to be installed
                  Depends: deskbar-applet but it is not going to be installed
                  Depends: ekiga but it is not going to be installed
                  Depends: gdebi but it is not going to be installed
                  Depends: gnome-power-manager but it is not going to be install ed
                  Depends: gnome-screensaver but it is not going to be installed
                  Depends: gnome-system-monitor but it is not going to be instal led
                  Depends: gnome-volume-manager but it is not going to be instal led
                  Depends: gnopernicus but it is not going to be installed
                  Depends: gok but it is not going to be installed
                  Depends: libgnomevfs2-bin but it is not going to be installed
                  Depends: libgnomevfs2-extra but it is not going to be installe d
                  Depends: openoffice.org-gnome but it is not going to be instal led
E: Broken packages


```

---

### Post by johnc4510 on 2006-06-04
Try these commands:
sudo aptitude update
sudo aptitude dist-upgrade

---

### Post by DDM on 2006-06-04
This happened to me once. Try this:
```
sudo nano /etc/apt/sources/list

Then take the # signs outof the lines that say deb http://blah

sudo apt-get update
```

---

### Post by lakelovers on 2006-06-04
[QUOTE=johnc4510]Try these commands:
sudo aptitude update
sudo aptitude dist-upgrade[/QUOTE]

Tried your suggestions. Still have "unmet dependencies."

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: alacarte but it is not going to be installed
                  Depends: deskbar-applet but it is not going to be installed
                  Depends: ekiga but it is not going to be installed
                  Depends: gdebi but it is not going to be installed
                  Depends: gnome-power-manager but it is not going to be installed
                  Depends: gnome-screensaver but it is not going to be installed
                  Depends: gnome-system-monitor but it is not going to be installed
                  Depends: gnome-volume-manager but it is not going to be installed
                  Depends: gnopernicus but it is not going to be installed
                  Depends: gok but it is not going to be installed
                  Depends: libgnomevfs2-bin but it is not going to be installed
                  Depends: libgnomevfs2-extra but it is not going to be installed
                  Depends: openoffice.org-gnome but it is not going to be installed

I looked at the instructions (top of the forum) for fixing dependencies but it's too complicated or not explicit enough for my meager brain. I'm about to give up and live with Breezy.

---

### Post by lakelovers on 2006-06-04
[QUOTE=DDM]This happened to me once. Try this:
```
sudo nano /etc/apt/sources/list

Then take the # signs outof the lines that say deb http://blah

sudo apt-get update
```[/QUOTE]

I've done that. Thanks for the response, anyway. I'm amazed I haven't cooked my system with as many things as I've tried. I'm wondering where all those files are that I have updated or upgraded more than once.
Jerry

---

