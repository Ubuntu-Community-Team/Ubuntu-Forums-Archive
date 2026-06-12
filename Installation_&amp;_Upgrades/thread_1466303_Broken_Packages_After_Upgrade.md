---
title: "Broken Packages After Upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Brodie337 on 2010-04-30
Hello there,

I'm a fairly basic user, so bear with me...

I recently upgraded to Ubuntu 10.04, (from 9.10) using the update-manager. However, during the installation there was an error during the 'Installing Packages' phase, which has left me with some broken packages, including initramfs-tools, and upstart. I suspect there may be more, but I have not come across them yet.

I've tried using "Fix broken packages" under "Edit" in Synaptic, but to no avail.

Is there any way to recover this install? I really don't want to do a fresh install.

Thanks in advance,
Brodie.

---

### Post by kansasnoob on 2010-04-30
I would try:

```
sudo apt-get clean
```

Then :

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Any error messages that the terminal displays may be very helpful.

---

### Post by Brodie337 on 2010-04-30
Thats the thing... There are no error messages.

I run that, and it comes up with nothing for "sudo apt-get clean"
and then after updating it simply says:
"0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

---

### Post by Brodie337 on 2010-04-30
Any ideas?

---

### Post by kansasnoob on 2010-04-30
Try:

```
sudo dpkg --configure -a
```

or possibly see what the following tells you:

```
sudo apt-get -f install
```

---

### Post by wme on 2010-04-30
so i upgraded from  9.10  to 10.04 nice 
but i had  my  computer  partition with windows 7 and   now when i boot up  
i cant  use  windows  7   it says  missing mbr helper can somone  help 
maybe  a  update  or  terminal command  could  fix  >? dont want to  loose my  data
:confused:

---

### Post by Brodie337 on 2010-04-30
OK, I've given that a crack, and "sudo dpkg --configure -a" doesn't return anything, it just takes me back to the prompt.

Here's the other one:
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by P4man on 2010-04-30
so what happens when you try to install something. Try this, just for us to get the output:

```
sudo apt-get install iotop
```

(iotop is just tiny network monitor, and harmless)

---

### Post by kansasnoob on 2010-04-30
> **wme said:**
> so i upgraded from  9.10  to 10.04 nice 
but i had  my  computer  partition with windows 7 and   now when i boot up  
i cant  use  windows  7   it says  missing mbr helper can somone  help 
maybe  a  update  or  terminal command  could  fix  >? dont want to  loose my  data
:confused:

It would be best to start your own thread, and since it's boot related include the output of the boot info script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Brodie337 on 2010-04-30
iotop installs OK:
```
sudo apt-get install iotop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  iotop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.0kB of archives.
After this operation, 168kB of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com/ubuntu/ lucid/universe iotop 0.4-1 [26.0kB]
Fetched 26.0kB in 1s (23.1kB/s)
Selecting previously deselected package iotop.
(Reading database ... 163231 files and directories currently installed.)
Unpacking iotop (from .../archives/iotop_0.4-1_all.deb) ...
Processing triggers for man-db ...
Setting up iotop (0.4-1) ...

Processing triggers for python-support ...

```

However, if we try something like usplash, which I do not have installed:

```
sudo apt-get install usplash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  usplash: Depends: initramfs-tools (>= 0.92bubuntu55) but it is not going to be installed
           Depends: upstart (>= 0.6.3-4) but it is not going to be installed
E: Broken packages

```

I attempt to install initramfs-tools...
```
sudo apt-get install initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
initramfs-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by wme on 2010-04-30
srry  i know  but i couldnt find  create   your  fourm  but i  would   really  appreciate your help   and i apologize
and that  script should  be  able to  alow me to boot back into  windows 7 
from grub dual  boot ?

---

### Post by kansasnoob on 2010-04-30
> **Brodie337 said:**
> Hello there,

I'm a fairly basic user, so bear with me...

I recently upgraded to Ubuntu 10.04, (from 9.10) using the update-manager. However, during the installation there was an error during the 'Installing Packages' phase, which has left me with some broken packages, including initramfs-tools, and upstart. I suspect there may be more, but I have not come across them yet.

I've tried using "Fix broken packages" under "Edit" in Synaptic, but to no avail.

Is there any way to recover this install? I really don't want to do a fresh install.

Thanks in advance,
Brodie.

So if you go to Synaptic, click on Custom Filters, then look under "Upgradable" or "Broken" does it show anything?

While in Synaptic click on the Settings > Repositories and see if anything looks haywire.

Also from Synaptic you can use the search feature, for instance type "initramfs-tools", then click on Package > Properties and see what versions are available and/or installed. Or alternately you can use:

```
aptitude show <package-name>
```

e.g.

```
lance@lance-desktop:~$ aptitude show initramfs-tools
Package: initramfs-tools
State: installed
Automatically installed: no
Version: 0.92bubuntu78
Priority: required
Section: utils
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 442k
Depends: initramfs-tools-bin (= 0.92bubuntu78), klibc-utils (>= 1.5.9-1),
         busybox-initramfs (>= 1:1.13.3-1ubuntu5), cpio, module-init-tools, udev
         (>= 147~-5), findutils (>= 4.2.24), util-linux (> 2.15~rc1)
Conflicts: usplash (< 0.5.50)
Breaks: mountall (< 2.0~)
Provides: linux-initramfs-tool
Description: tools for generating an initramfs
 This package contains tools to create and boot an initramfs for packaged 2.6
 Linux kernel. The initramfs is a gzipped cpio archive. At boot time, the kernel
 unpacks that archive into RAM, mounts and uses it as initial root file system.
 The mounting of the real root file system occurs in early user space. klibc
 provides utilities to setup root. Having the root on EVMS, MD, LVM2, LUKS or
 NFS is also supported. Any boot loader with initrd support is able to load an
 initramfs archive.

lance@lance-desktop:~$ aptitude show upstart
Package: upstart
State: installed
Automatically installed: no
Version: 0.6.5-6
Priority: required
Section: admin
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 819k
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.2.16), libnih-dbus1 (>= 1.0.0),
         libnih1 (>= 1.0.0), libudev0 (>= 151-5), sysvinit-utils, sysv-rc,
         initscripts, mountall, ifupdown (>= 0.6.8ubuntu29)
Conflicts: startup-tasks, system-services, sysvinit, upstart-compat-sysv,
           upstart-job
Replaces: startup-tasks, system-services, sysvinit, upstart-compat-sysv,
          upstart-job
Provides: startup-tasks, system-services, upstart-compat-sysv, upstart-job
Description: event-based init daemon
 upstart is a replacement for the /sbin/init daemon which handles starting of
 tasks and services during boot, stopping them during shutdown and supervising
 them while the system is running.
Homepage: http://upstart.ubuntu.com/

lance@lance-desktop:~$ 

```

---

### Post by kansasnoob on 2010-04-30
> **wme said:**
> srry  i know  but i couldnt find  create   your  fourm  but i  would   really  appreciate your help   and i apologize
and that  script should  be  able to  alow me to boot back into  windows 7 
from grub dual  boot ?

At the top of the forum page click on Installation & Upgrades. In the somewhat upper left hand corner you'll see the option to Start new thread.

The Boot Info Script will not fix anything but it will provide us with the info we need to troubleshoot the problem.

---

### Post by Brodie337 on 2010-04-30
There's nothing at all showing up under the "Broken" filter.

Theres what I get using aptitude show.

```
[user @ ~] aptitude show initramfs-tools
Package: initramfs-tools
State: installed
Automatically installed: no
Version: 0.92bubuntu78
Priority: required
Section: utils
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 442k
Depends: initramfs-tools-bin (= 0.92bubuntu78), klibc-utils (>= 1.5.9-1),
         busybox-initramfs (>= 1:1.13.3-1ubuntu5), cpio, module-init-tools, udev
         (>= 147~-5), findutils (>= 4.2.24), util-linux (> 2.15~rc1)
Conflicts: usplash (< 0.5.50)
Breaks: mountall (< 2.0~)
Provides: linux-initramfs-tool
Description: tools for generating an initramfs
 This package contains tools to create and boot an initramfs for packaged 2.6
 Linux kernel. The initramfs is a gzipped cpio archive. At boot time, the kernel
 unpacks that archive into RAM, mounts and uses it as initial root file system.
 The mounting of the real root file system occurs in early user space. klibc
 provides utilities to setup root. Having the root on EVMS, MD, LVM2, LUKS or
 NFS is also supported. Any boot loader with initrd support is able to load an
 initramfs archive.

[user @ ~] aptitude show upstart
Package: upstart
State: installed
Automatically installed: no
Version: 0.6.5-6
Priority: required
Section: admin
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 819k
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.2.16), libnih-dbus1 (>= 1.0.0),
         libnih1 (>= 1.0.0), libudev0 (>= 151-5), sysvinit-utils, sysv-rc,
         initscripts, mountall, ifupdown (>= 0.6.8ubuntu29)
Conflicts: startup-tasks, system-services, sysvinit, upstart-compat-sysv,
           upstart-job
Replaces: startup-tasks, system-services, sysvinit, upstart-compat-sysv,
          upstart-job
Provides: startup-tasks, system-services, upstart-compat-sysv, upstart-job
Description: event-based init daemon
 upstart is a replacement for the /sbin/init daemon which handles starting of
 tasks and services during boot, stopping them during shutdown and supervising
 them while the system is running.
Homepage: http://upstart.ubuntu.com/

```

---

### Post by P4man on 2010-04-30
There seems nothing wrong with your package manager. usplash is not supported on lucid. Im thinking your software sources may have entries for karmic that you manually added.

Can you post the contents of 

/etc/apt/sources.list

---

### Post by Brodie337 on 2010-04-30
```
# deb cdrom:[Ubuntu 9.10 _lucid Koala_ - Release i386 (20091028.5)]/ lucid main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ lucid multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ lucid universe
deb http://au.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://au.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://hr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://hr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://au.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe #Added by software-properties
deb http://au.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://au.archive.ubuntu.com/ubuntu/ lucid-security multiverse

# deb http://ppa.launchpad.net/bisigi/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu lucid main
```

---

### Post by P4man on 2010-04-30
that looks okay as well, but it seems third party repositories are no longer in there, but moved to /etc/apt/sources.list.d/

Perhaps post the output of

```
ls /etc/apt/sources.list.d/
```

or check the "other software"  tab in system > adminstration > software sources.  Disable anything you dont know you need (and if there is something you need, post it here)

---

### Post by Brodie337 on 2010-04-30
ls /etc/apt/sources.list.d/ returns nothing at all.

There's no other sources under "Other", apart from the standard Lucid repos.

---

### Post by P4man on 2010-04-30
Well, then Im running out of ideas then. But remind me, what is the problem exactly? I do get slightly different messages than you trying to install invalid or unavailable packages, but it seems you can update and install and remove apps that are actually available and installable, so whats the problem again (serious question, sounds more rhetorical than i mean it) ?

---

### Post by Brodie337 on 2010-04-30
It appeared that there were broken packages after an upgrade to 10.04 failed (Sort of). The nly thing wrong with it was that when I rebooted, there was no splash screen, so I assumed usplash must be missing. Now I can see I should have been trying to install plymouth (facepalm!) instead, and thats why it was telling me that initramfs was broken.

Thanks to everyone for taking the time to put up with a newbie like myself!

---

### Post by P4man on 2010-04-30
> **Brodie337 said:**
> It appeared that there were broken packages after an upgrade to 10.04 failed (Sort of). The nly thing wrong with it was that when I rebooted, there was no splash screen, so I assumed usplash must be missing. Now I can see I should have been trying to install plymouth (facepalm!) instead, and thats why it was telling me that initramfs was broken.

Thanks to everyone for taking the time to put up with a newbie like myself!

You might have had broken packages,but it looks like its fixed now. And indeed, lucid uses plymouth. If you dont get the splash screen try this:

```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/plymouth 
``` followed by:
```
sudo update-initramfs -u
```

That will slow your boot a tiny bit (like 0.5s) but might fix it (it did for me)

---

### Post by charlesopondo on 2010-05-07
This worked very well for me, and actually reduced my boot time substantially. The echo command was failing, though, even with sudo, so using the terminal I manually created the file:

```
sudo pico /etc/initramfs-tools/conf.d/splash
```

then inserted the text:

```
FRAMEBUFFER=y
```

exited, saving changes, then back to the terminal:

```
sudo update initramfs -u
```

and on rebooting saw the lovely Plymouth for the first time!

---

