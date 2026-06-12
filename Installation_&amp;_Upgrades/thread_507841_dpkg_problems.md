---
title: "dpkg problems"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by cbaumann on 2007-07-23
Right, I know there have been posts about it already. Yet the problem hasn't been solved for me.

First of, I have upgraded to Feisty lately.

So this is what I get when I run some apt-get install 
> 
~$ sudo apt-get install weechat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  weechat
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 17.4kB of archives.
After unpacking 69.6kB of additional disk space will be used.
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe weechat 0.2.3-1 [17.4kB]
Fetched 17.4kB in 0s (60.5kB/s)
Selecting previously deselected package weechat.
(Reading database ... 147230 files and directories currently installed.)
Unpacking weechat (from .../weechat_0.2.3-1_all.deb) ...
Setting up acpid (1.0.4-5ubuntu6) ...
 * Loading ACPI modules...                                                                                                             [ OK ] 
 * Starting ACPI services...                                                                                                                  invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up weechat (0.2.3-1) ...
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 gnome-power-manager
 gnome-session
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


I already tried dpkg --configure -a and all that, still the same. 
If it's something very very obvious, just slap me and give me a hint, if not, then no slap needed. :-)

Thanks in advance,

---

### Post by davidjmayo on 2007-07-23
just a hint

from the top of your output
~$ sudo apt-get install weechat
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
weechat
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
**6 not fully installed or removed.**
Need to get 17.4kB of archives.
After unpacking 69.6kB of additional disk space will be used.
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe weechat 0.2.3-1 [17.4kB]
Fe

Looking further down your list all the errors are for dependency problems
Now this may sound like a stupid question but are you in Canada or using the Canada repos because there have been problems with them yesterday/today.

---

### Post by Seisen on 2007-07-23
Did you try

```
sudo apt-get -f install
```

---

### Post by cbaumann on 2007-07-23
Yep. Didn't help.

However I kind of solved it myself. 

I removed and then reinstalled the following packages using Synaptic
> acpid
acpi-support
powermanagement-interface
gnome-power-manager
gnome-session
ubuntu-desktop


It seems to work again! Yey! :-)

Thanks to you lot :)

---

