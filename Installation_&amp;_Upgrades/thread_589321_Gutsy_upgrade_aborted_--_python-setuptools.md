---
title: "Gutsy upgrade aborted -- python-setuptools"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by graybark on 2007-10-24
So I got the dreaded "The upgrade aborts now. Your system could be in an unusable state." with supposedly 25 minutes to go in the installation phase.  The tail end of my term.log is:

```
Setting up x-window-system-core (1:7.2-5ubuntu13) ...
Setting up xsane (0.99+0.991-3ubuntu5) ...
Setting up brltty (3.7.2-7.1ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Setting up brltty-x11 (3.7.2-7.1ubuntu1) ...
Setting up scim (1.4.7-1ubuntu2) ...
Installing new version of config file /etc/scim/config ...
Installing new version of config file /etc/X11/xinit/xinput.d/scim ...
Setting up scim-modules-table (0.5.7-1ubuntu2) ...
Setting up scim-tables-additional (0.5.7-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
Errors were encountered while processing:
 python-setuptools
 python-opengl
Traceback (most recent call last):
  File "logging/__init__.py", line 753, in emit
  File "logging/__init__.py", line 731, in flush
IOError: [Errno 9] Bad file descriptor
/home/username/.themes/username/gtk-2.0/gtkrc:46: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/username/.themes/username/gtk-2.0/gtkrc:47: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/username/.themes/username/gtk-2.0/gtkrc:48: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
gutsy: Fatal IO error 9 (Bad file descriptor) on X server :0.0.
Setting up python-setuptools (0.6c6-1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/setuptools.pth
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/setuptools.pth
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-opengl:
 python-opengl depends on python-setuptools; however:
  Package python-setuptools is not configured yet.
dpkg: error processing python-opengl (--configure):
 dependency problems - leaving unconfigured
```

Restarting Update Manager did nothing terribly useful -- it seems to think everything is up to date.  It did show an ipython package greyed-out, making me think that package might be causing trouble (not sure what repo I pulled it from), so I removed it.  I then removed and re-installed the two packages that had problems mentioned in term.log -- python-setuptools and python-opengl.  After reading the forums here a bit I ran the command to init the kernal ramdisk or whatever so that hopefully the new kernel will boot (though I haven't tried it yet).  I also ran all the various apt-get update/upgrade/autoremove/clean and they finish cleanly, mostly doing nothing (autoremove did remove some stuff).

So I'm wondering -- how likely is it I'll have a working system if I try a reboot?  Was that drastic abort message the result of just two fairly minor packages failing to upgrade cleanly?  Do I need to be overly concerned that the cleanup phase didn't get a chance to run?  Any insights would be appreciated.

---

### Post by graybark on 2007-10-24
Well, a power outage answered the what'll happen when I reboot question.  Answer: nothing too terribly bad.  Kernel booted, screen resolution was wrong but easily fixed.  However cpu was at 100%, system monitor showed udevd the culprit.  Googling around brought me to this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/115616](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/115616)

Apparently evms should have been removed by the upgrade but it wasn't.  Maybe that is something that would have happened after the point where the upgrade decided to abort, though my logs show evms was upgraded during the process, so then removing it sounds a little odd.  Anyway removing evms and rebooting fixed that.  

Trying to confirm that the cpu usage issue was fixed by opening up the system monitor revealed the next issue, which is that opening the system monitor leads to high CPU and an infinite supply of these messages in the kernel log:

pci_set_power_state(): 0000:02:0c.0: state=3, current state=5

Googling around for that shows it's an oldie (I see mention of it as far back as 11/2006), somehow related to network monitoring, avoided by just not opening Gnome sysmon.  Guess I'll use top when I need it instead of the graphical interface.

All in all, not a great upgrade experience, and continuing a trend of upgrades that used to work fine now causing more and more problems.  My upgrade from whatever was before Dapper to Dapper was flawless, as was Dapper to Edgy.  Edgy to Feisty removed mod_python even though I was using it, so my web server was dead until I re-installed mod_python (why was it dropped by the upgrade?).  Then Feisty to Gutsy upgrade aborted.  Maybe I've done too many upgrades without a fresh install?  But I'd really rather not to a fresh install, I've got a database, web server, svn repo on this machine and I'd rather not set them all back up from scratch (though yes, I have them all backed up and could do it if necessary).

---

