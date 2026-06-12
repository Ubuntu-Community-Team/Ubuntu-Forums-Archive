---
title: "The debootstrap program exited...."
date: 2006-04-01
forum: Installation &amp; Upgrades
---

### Post by gwyrlim on 2006-04-01
...with an error (return value 1).

Hi. 
At 34% of the installation of the base system I get this error message. I have tried reburn at lower speed and on another CD brand. I have installed the system on vmware using the iso with out problem so I think its ok. Used md5sum and it’s ok. I have tried another HD and changing the keyb from usb to ps/2. I have tried enable DMA on the DVD-ROM and using English during installation. I have tried different file systems and partition "layouts". I have tried ubuntu 5.04 and got the same error.](*,) 

I have search the net but probably missed something because I can’t get this to work.

Looking in the console Alt-F3 gives this message in 5.10 and in 5.04.This is only the last part.

Selecting previously deselected package debconf.
(Reading database ... 2474 files and directories currently installed.)
Unpacking debconf (from .../debconf_1.4.56ubuntu2_all.deb) ...
dpkg: debconf: dependency problems, but configuring anyway as you request:
 debconf depends on debconf-i18n | debconf-english; however:
  Package debconf-i18n is not installed.
  Package debconf-english is not installed.
Setting up debconf (1.4.56ubuntu2) ...
/var/lib/dpkg/info/debconf.postinst: line 80: 22494 Segmentation fault      $PYTHON -O /usr/lib/$PYTHON/compileall.py -q $i
dpkg: error processing debconf (--install):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 debconf

I managed to save all the log files, hardware-summery, messages, partman and syslog but I can’t get anything use full from them. I’m a noob in this area.

The system is an Abit kx7-333 with a AMD 2400+ M, 2Gig mem, HD 129G Deskstar, Leadtek 6800LE.

What have I missed?:-k

---

### Post by Sef on 2006-04-02
Have you tried using Breezy 5.10 Live CD and see if you get the same problem?

If you do,  i would suspect a problem with your hardware.  If not, then I would suspect the install disk, but since you have used it to install on another system, I don't think it would be the problem.

---

### Post by gwyrlim on 2006-04-02
I can run the live CD using expert mode to tweak the resolution other wise it uses an resolution my monitor can&#8217;t display. I think it uses something other than 60Hz . The root password got messed up but that was probably me doing something wrong during startup.

---

