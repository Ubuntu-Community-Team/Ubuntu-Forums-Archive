---
title: "Linux Headers issues"
date: 2019-11-16
forum: Installation &amp; Upgrades
---

### Post by celticfire on 2019-11-16
I've been same issues with my system and I can't upgrade as I continually get this error:

E: The package linux-headers-4.4.0-141 needs to be reinstalled, but I can't find an archive for it.

even when attempting to reinstall with the following command:
sudo apt install --reinstall linux-headers-generic

I continue to get the error above.

Couple of odd things to note, when I run a list of the packages I get the following:

 dpkg --list | grep linux-image
ii  linux-image-4.4.0-139-generic               4.4.0-139.165                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
pi  linux-image-4.4.0-141-generic               4.4.0-141.167                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-139-generic         4.4.0-139.165                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
pi  linux-image-extra-4.4.0-141-generic         4.4.0-141.167                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
pi  linux-image-generic                         4.4.0.141.147                                amd64        Generic Linux kernel image

When I run uname -r I get this:
uname -r
4.4.0-139-generic


Anyone have any ideas?  I seem to keep going in circles attempting to upgrade but can't reinstall the headers.  All insight welcome, thanks in advance.

---

### Post by TheFu on 2019-11-16
4.4 is from the original 16.04 install.  If you aren't tied to it, 4.15 is available and has been for a very long time.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I'm on this across all my production ubuntu servers and desktops.
```
ii  linux-image-4.15.0-66-generic               4.15.0-66.75~16.04.1                         amd64        Signed kernel image generic
ii  linux-image-4.15.0-70-generic               4.15.0-70.79~16.04.1                         amd64        Signed kernel image generic
```

---

### Post by celticfire on 2019-11-17
Thanks for the reply, but it look like something is corrupt in my kernel installation/configuration as even when I attempt to upgrade from the link provided I still get the same error:

sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04 
Reading package lists... Done
Building dependency tree... Done
E: The package linux-headers-4.4.0-141 needs to be reinstalled, but I can't find an archive for it.

---

### Post by TheFu on 2019-11-17
Dumb question - did a **sudo apt update** get run just before?
```
$ sudo apt search linux-headers-4.4.0-141
Sorting... Done
Full Text Search... Done
linux-headers-4.4.0-141/xenial-updates,xenial-updates,xenial-security,xenial-security 4.4.0-141.167 all
  Header files related to Linux kernel version 4.4.0

linux-headers-4.4.0-141-generic/xenial-updates,xenial-security 4.4.0-141.167 amd64
  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP

linux-headers-4.4.0-141-lowlatency/xenial-updates,xenial-security 4.4.0-141.167 amd64
  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
```
Do you have at least 1 of those repos enabled?

Do you normally patch weekly?  Getting into APT-hell can happen in a few different ways. Patching weekly, avoiding direct .deb file installations, and limiting the use of PPAs to just a few, reputable, PPAs per system is the easiest way to avoid APT issues.
Even if you do those things perfectly, having versioned backups that you can restore from yesterday, 3 weeks ago, 2 months ago is always helpful.  Had a DB get corrupted when a new nextcloud update broken some things.  Took me a few weeks to notice, because the core things for which I used nextcloud still worked fine.  Anyway, I looked through to changes in the backups to find the DB modification and had to go back 35 days.  If I didn't have 90 days of daily, automatic, versioned, backups, I'd have to start all over with nextcloud and the 15 apps installed inside. As it was, it took me a few times to figure out which app had broken things.

---

### Post by ubfan1 on 2019-11-17
4.4.0-141 is a pretty old version.  the only reason I can think of using it is the API change which occurred about that time (I thought 142 was the old API, but don't recall).  Are you trying to builld a driver which fails with the newer headers?

---

### Post by celticfire on 2019-11-17
It's actually kind of strange, I haven't done anything to the system but I keep these errors.  I also noticed this when I open software-properties-gtk

sudo software-properties-gtk

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 1171, in detect_drivers
    self.apt_cache = apt.Cache()
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 113, in __init__
    self.open(progress)
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 165, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package linux-headers-4.4.0-141 needs to be reinstalled, but I can't find an archive for it.

Does seem like there is some type of driver issue that is reliant on those headers but it is in some corrupted state.  I also can't view any drivers that installed in the software-properties-gtk UI.  Any ideas what I should do at this point? seems like everytime I attempt any type of upgrade or install I get that error (SystemError: E:The package linux-headers-4.4.0-141 needs to be reinstalled, but I can't find an archive for it.)

---

### Post by ubfan1 on 2019-11-17
The header package dpkg "actons" are "p" whichis purge.  If you had manually deleted some of those files, maybe the purge is getting confused.  Manually try a sudo apt-get purge linux-image-generic                         4.4.0.141.147 and for any complaints about "missing files" ,  just use touch to make them (zero length is OK).  When you get rid of all the "p" actions, then try an install .

---

### Post by celticfire on 2019-11-17
Same thing:

sudo apt-get purge linux-image-generic 4.4.0.141.147
Reading package lists... Done
Building dependency tree... Done
E: The package linux-headers-4.4.0-141 needs to be reinstalled, but I can't find an archive for it.

---

### Post by ubfan1 on 2019-11-17
Confirm that you are running Ubuntu 16.04, and post your /etc/apt/sources.list. Also apt-cache policy  linux-headers-4.4.0-141

---

### Post by TheFu on 2019-11-17
Are these canonical repos in your APT sources?
xenial-updates,xenial-updates,xenial-security,xenial-security

BTW, running any GUI program using sudo is a bad idea.  Always use **sudo -H**,  if you must.

---

### Post by Doug S on 2019-11-18
With caution, try [this]("https://stackoverflow.com/questions/48431372/removing-broken-packages-in-ubuntu"), which I am copying below:


   [LIST=1]
[*] Find your package in /var/lib/dpkg/info, for example using: ls -l /var/lib/dpkg/info | grep <package>


[*]    Move the package folder to another location:

        sudo mv /var/lib/dpkg/info/<package>.* /tmp/


[*]    Run the following command:

        sudo dpkg --remove --force-remove-reinstreq <package>
[/LIST]

---

